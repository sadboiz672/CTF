## **1. Grab a beer and disappear**
- Tôi nghĩ đây là 1 thử thách bị lỗi đề, bởi cần phải  hợp 3 ổ vào thay vì sử dụng strings là ra flag 🩹

![image](https://user-images.githubusercontent.com/42565778/206955158-4bcf0baa-51b6-417f-9476-54c5778dd1fb.png)

`Flag: HCTF{n3ver_G1v3_4_Pc_t0_druNk_p30pL3!!}`




## **2. New cocktail**
- Theo mô tả của đề bài tôi chích 1 vài keyword để thực hiện tìm kiếm, có vẻ thử thách này cần thu thập thông tin từ nội dung các cuộc trò chuyện trong mail

![image](https://user-images.githubusercontent.com/42565778/206955736-9ed28281-a24b-4701-8951-36d6c7b0d69b.png)
 
- Sử dụng tree để tìm kiếm thông tin liên quan

![image](https://user-images.githubusercontent.com/42565778/206955861-e746436d-9827-4efb-a9ca-f62bac05200c.png)

=> Tập trung phân tích file **INBOX**

- Lướt qua toàn bộ thông tin, tôi có thể thấy được cuộc trò chuyện với hacker có địa chỉ email:

![image](https://user-images.githubusercontent.com/42565778/206956576-243b5a23-bfa1-4fce-adec-bcce487d3d01.png)

- Grep: **hackappapub@gmail.com**

![image](https://user-images.githubusercontent.com/42565778/206956733-a53b2573-5f25-42a1-aec4-d48154f7d8a6.png)

- Thông thường các kiểu tấn công qua mail sẽ là **phishing**, chủ yếu là khai thác thông qua click vào link độc hại hoặc download một tệp tin gì đó về máy. Và tất nhiên chúng ta cần phải xác định điều này, grep **http://** or **https://** or **http**

![image](https://user-images.githubusercontent.com/42565778/206957563-6c4839e2-2b0c-4f81-942f-f1344b9e6414.png)

- truy cập https://we.tl/t-rA3crW7ubH và lấy file về, sau đó dùng ftk để mở file iso, fla được ẩn trong bức ảnh

![image](https://user-images.githubusercontent.com/42565778/206958098-10fee7a7-4bfd-4a20-bb2b-ee9b5827dedb.png)

`Flag: HCTF{4_c0ck74il_t0_.....}`




## **3. Hook**
- Đây là cuộc hội thoại trao đổi với giao thức **SMTP**, để có thể điều tra được chúng ta cần phải khoanh vùng các thông tin đặc biệt. Tôi nhận ra trong cuộc hội thoại với độ dài length các stream khá nhỏ nhưng tới cuối cùn thì có stream với length rất lớn và khả nghi. Cần kiểm tra nội dung đang được vận chuyển là gì

![image](https://user-images.githubusercontent.com/42565778/206959140-b56b46e3-d3e6-4d95-8eed-036b1e813727.png)

- Nếu không biết nhiều về các công cụ hỗ trợ hoặc chưa có kinh nhiệm thì khá là khó để nhận biết, có lẽ **cyberchef** là cái gì đó khá mạnh mẽ :))

![image](https://user-images.githubusercontent.com/42565778/206959285-deffc94e-e630-477a-845b-800674bc1b25.png)

`Flag: HCTF{u_4r3_1N_.....}`




## **4. Hidden cocktails**
- Một thử thách liên quan tới NTFS file system

![image](https://user-images.githubusercontent.com/42565778/206960063-58d96f37-ba19-40d0-964c-b5f866b27986.png)

sau khi tham khảo từ nhiều nguồn và tôi nghĩ đây là [bài viết]([url](https://www.secjuice.com/ntfs-steganography-hiding-in-plain-sight/)) hữu ích và demo cho mọi người 

![image](https://user-images.githubusercontent.com/42565778/206960662-b37afd90-a21b-44f8-b56e-182f46702524.png)

Giờ thử truy vấn bằng cmd: cmd /F

![image](https://user-images.githubusercontent.com/42565778/206960869-c51a33df-cd34-4aa3-9c75-ef74fc94aad1.png)

-sau khi thử các thông tin có trong file và đều là các hint vớ vẩn, nên tập trung vào folder book để tìm kiếm, cmd **dir /r**, có 1 file đã bị ẩn

![image](https://user-images.githubusercontent.com/42565778/206961077-be37fb65-2d38-476a-a108-54c558110d1b.png)

- Bạn có thể mở nó với notepad hoặc mở trực tiếp với cmd **more**

![image](https://user-images.githubusercontent.com/42565778/206961191-f5d2b2c9-3c07-4011-932e-e58601af0d20.png)


`Flag: hctf{4lt3rn4t3_D4t4_Str34m_.....}`





