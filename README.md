<p align="center">
 <h1 align="center">Tổng quan Docker</h1>
</p>

# Docker là gì?

- Docker là một nền tảng mã nguồn mở cho phép các nhà phát triển xây dựng, triển khai, chạy, cập nhật và quản lý containers—standardized 
- Docker làm cho  quá trình container hóa  nhanh hơn, dễ dàng hơn và an toàn hơn
- cho phép tạo các môi trường độc lập và tách biệt để khởi chạy và phát triển ứng dụng và môi trường này được gọi là container.

# Cách thức hoạt động của container?

- Docker hoạt động bằng cách cung cấp phương thức tiêu chuẩn để chạy mã của bạn. 
- Docker là hệ điều hành dành cho container. 
- Docker tương tự như cách máy ảo ảo hóa (loại bỏ nhu cầu quản lý trực tiếp) phần cứng máy chủ, các container sẽ ảo hóa hệ điều hành của máy chủ. - - Docker được cài đặt trên từng máy chủ và cung cấp các lệnh đơn giản mà bạn có thể sử dụng để dựng, khởi động hoặc dừng container.
-  công nghệ container cung cấp tất cả các chức năng và lợi ích của máy ảo bao gồm cách ly ứng dụng, khả năng mở rộng hiệu quả về chi phí và khả năng dùng một lần—cùng với các lợi thế bổ sung quan trọng:
  + Trọng lượng nhẹ hơn máy ảo
  + Cải thiện năng suất của nhà phát triển
  + Hiệu quả sử dụng tài nguyên cao hơn
  
# Tại sao nên sử dụng Docker?

- Việc setup và deploy application lên một hoặc nhiều server rất vất vả từ việc phải cài đặt các công cụ, môi trường cần cho application đến việc chạy được ứng dụng chưa kể việc không đồng nhất giữa các môi trường trên nhiều server khác nhau.
- Docker cho phép các nhà phát triển truy cập các khả năng chứa riêng này bằng cách sử dụng các lệnh đơn giản và tự động hóa chúng thông qua giao diện lập trình ứng dụng (API) tiết kiệm công việc. Docker cung cấp:
 + Tính di động của bộ chứa được cải thiện và liền mạch
 + Trọng lượng nhẹ hơn và cập nhật chi tiết 
 + Tự động tạo vùng chứa
 + Theo dõi các phiên bản
 + Tái sử dụng vùng chứa
 +  Nhà phát triển có thể truy cập sổ đăng ký nguồn mở chứa hàng nghìn vùng chứa do người dùng đóng góp

# Các công cụ và thuật ngữ Docker

- DockerFile:  là một file dạng text không có phần đuôi mở rộng, chứa các đặc tả về một trường thực thi phần mềm, cấu trúc cho Docker Image
- Docker Image: là một file bất biến - không thay đổi, chứa các source code, libraries, dependencies, tools và các files khác cần thiết cho một ứng dụng để chạy
- Docker Client: là cách mà bạn tương tác với docker thông qua command trong terminal. Docker Client sẽ sử dụng API gửi lệnh tới Docker Daemon.
- Docker Daemon: là server Docker cho yêu cầu từ Docker API. Nó quản lý images, containers, networks và volume.
- Docker Volumes: là cách tốt nhất để lưu trữ dữ liệu liên tục cho việc sử dụng và tạo apps.
- Docker Registry: là nơi lưu trữ riêng của Docker Images. Images được push vào registry và client sẽ pull images từ registry. Có thể sử dụng registry của riêng bạn hoặc registry của nhà cung cấp như : AWS, Google Cloud, Microsoft Azure.
- Docker Hub: là Registry lớn nhất của Docker Images ( mặc định). Có thể tìm thấy images và lưu trữ images của riêng bạn trên Docker Hub ( miễn phí).
- Docker Repository: là tập hợp các Docker Images cùng tên nhưng khác tags. VD: golang:1.11-alpine.
- Docker Networking: cho phép kết nối các container lại với nhau. Kết nối này có thể trên 1 host hoặc nhiều host.
- Docker Compose: là công cụ cho phép run app với nhiều Docker containers 1 cách dễ dàng hơn. Docker Compose cho phép bạn config các command trong file docker-compose.yml để sử dụng lại. Có sẵn khi cài Docker.
- Docker Swarm: để phối hợp triển khai container.
- Docker Services: là các containers trong production. 1 service chỉ run 1 image nhưng nó mã hoá cách thức để run image — sử dụng port nào, bao nhiêu bản sao container run để service có hiệu năng cần thiết và ngay lập tức.

# Thiết lập Docker trên  máy tính 

- Trên Windows, cài Docker Desktop Installer theo link này: https://desktop.docker.com/win/stable/Docker Desktop Installer.exe, có nhiều options nhưng tôi khuyến khích chọn theo recommendation.
- Bạn có thể xem chi tiết cách cài đặt cho [Mac](https://docs.docker.com/desktop/install/mac-install/ ) , [Linux](https://docs.docker.com/engine/install/ubuntu/) và [Windows](https://docs.docker.com/desktop/install/windows-install/).

# Các câu lệnh thông dụng trong docker 

- docker ps: Dùng để liệt kê ra các container đang chạy. Khi sử dụng với các tham số
> -a/-all: Liệt kê tất cả các container, kể cả đang chạy hay đã kể thúc -q/-quiet: chỉ liệt kê ra id của các container.

```
$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

- docker pull: Docker Hub chứa rất nhiều các image được dựng sẵn, mà ta có thể pull về và dùng mà không cần phải định nghĩa và cấu hình lại từ đầu.

```
$ docker pull busybox
```

- docker images:  sử dụng lệnh để xem danh sách tất cả các image trên hệ thống của mình

```
$ docker images
REPOSITORY              TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
busybox                 latest              c51f86c28340        4 weeks ago         1.109 MB
```

- docker run: Lệnh này dùng để chạy một container dựa trên một image mà ta có sẵn. Ta có thể thêm vào sau lệnh này một vài câu lệnh khác như -it bash để chạy bash từ container này.

```
$ docker run busybox
```

- docker ps: hiển thị cho bạn tất cả các vùng chứa hiện đang chạy.

```
$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                      PORTS               NAMES
305297d7a235        busybox             "uptime"            11 minutes ago      Exited (0) 11 minutes ago                       distracted_goldstine
ff0a5c3750b9        busybox             "sh"                12 minutes ago      Exited (0) 12 minutes ago                       elated_ramanujan
14e5bd11d164        hello-world         "/hello"            2 minutes ago       Exited (0) 2 minutes ago                        thirsty_euclid
```

-docker stop: Lệnh này dùng để stop một hoặc nhiều container. Ngoài ra ta có thể dung docker kill để bắt buộc container dừng lại.

```
$ docker stop <list_container_name_or_id>
```

- docker build: Lệnh này dùng để build một image từ Dockerfile và context. Context ở đây là một tập file được xác đinh bởi đường dẫn hoặc url cụ thể. Ta có thể sử dụng thêm tham số -t để gắn nhãn cho image.

```
$ docker build -t your_name_container
```

- docker rm: Lệnh này dùng để xóa một hoặc nhiều container.

```
$ docker rm <list_container_name_or_id>
```

# Dockerfile

- Dockerfile là một tệp văn bản đơn giản chứa danh sách các lệnh mà ứng dụng khách Docker gọi trong khi tạo một image 
-  Để bắt đầu, hãy tạo một tệp trống mới trong trình soạn thảo văn bản yêu thích của chúng tôi và lưu tệp đó vào cùng thư mục với ứng dụng bình có tên là Dockerfile
- Các config :
  + FROM — chỉ định image gốc: python, unbutu, alpine…
  + LABEL — cung cấp metadata cho image. Có thể sử dụng để add thông tin maintainer. Để xem các label của images, dùng lệnh docker inspect.
  + ENV — thiết lập một biến môi trường.
  + RUN — Có thể tạo một lệnh khi build image. Được sử dụng để cài đặt các package vào container.
  + COPY — Sao chép các file và thư mục vào container.
  + ADD — Sao chép các file và thư mục vào container.
  + CMD — Cung cấp một lệnh và đối số cho container thực thi. Các tham số có thể được ghi đè và chỉ có một CMD.
  + WORKDIR — Thiết lập thư mục đang làm việc cho các chỉ thị khác như: RUN, CMD, ENTRYPOINT, COPY, ADD,…
  + ARG — Định nghĩa giá trị biến được dùng trong lúc build image.
  + ENTRYPOINT — cung cấp lệnh và đối số cho một container thực thi.
  + EXPOSE — khai báo port lắng nghe của image.
  + VOLUME — tạo một điểm gắn thư mục để truy cập và lưu trữ data.

- ví dụ: 

Chúng tôi bắt đầu với việc chỉ định hình ảnh cơ sở của chúng tôi. Sử dụng từ khóa FROM 

```
FROM python:3.8
```

Bước tiếp theo thường là viết các lệnh sao chép tệp và cài đặt các phụ thuộc. Đầu tiên, chúng tôi thiết lập một thư mục làm việc và sau đó sao chép tất cả các tệp cho ứng dụng của chúng tôi.

```
# đặt thư mục cho ứng dụng
WORKDIR /usr/src/app

# sao chép tất cả các tệp vào vùng chứa
COPY . .
```

Bây giờ, chúng tôi có các tệp, chúng tôi có thể cài đặt các phụ thuộc.

```
# install dependencies
RUN pip install --no-cache-dir -r requirements.txt
```

Điều tiếp theo chúng ta cần chỉ định là số cổng cần được hiển thị. Vì ứng dụng bình của chúng tôi đang chạy trên cổng 5000, đó là những gì chúng tôi sẽ chỉ ra.

```
EXPOSE 5000

```

Bước cuối cùng là viết lệnh để chạy ứng dụng, đơn giản là - python ./app.py. Chúng tôi sử dụng lệnh CMD 

```
CMD ["python", "./app.py"]
```

Mục đích chính của CMD là báo cho vùng chứa lệnh nào nó sẽ chạy khi nó được khởi động. Với điều đó, chúng tôi Dockerfile đã sẵn sàng. 

```
FROM python:3.8

# đặt thư mục cho ứng dụng
WORKDIR /usr/src/app

# sao chép tất cả các tệp vào vùng chứa
COPY . .

# cài đặt phụ thuộc
RUN pip install --no-cache-dir -r requirements.txt

# xác định số cổng mà vùng chứa sẽ hiển thị
EXPOSE 5000

# lệnh chạy
CMD ["python", "./app.py"]
```

Bây giờ chúng ta đã có Dockerfile, chúng ta có thể xây dựng hình ảnh của mình. Lệnh docker buildthực hiện công việc nặng nhọc là tạo hình ảnh Docker từ tệp Dockerfile

```
$ docker build -t yourusername/catnip .
Sending build context to Docker daemon 8.704 kB
Step 1 : FROM python:3.8
# Executing 3 build triggers...
Step 1 : COPY requirements.txt /usr/src/app/
 ---> Using cache
Step 1 : RUN pip install --no-cache-dir -r requirements.txt
 ---> Using cache
Step 1 : COPY . /usr/src/app
 ---> 1d61f639ef9e
Removing intermediate container 4de6ddf5528c
Step 2 : EXPOSE 5000
 ---> Running in 12cfcf6d67ee
 ---> f423c2f179d1
Removing intermediate container 12cfcf6d67ee
Step 3 : CMD python ./app.py
 ---> Running in f01401a5ace9
 ---> 13e87ed1fbc2
Removing intermediate container f01401a5ace9
Successfully built 13e87ed1fbc2
```

bạn có thể chạy thử image của mình như sau:

```
$ docker run -p 8888:5000 yourusername/catnip
 * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
```
