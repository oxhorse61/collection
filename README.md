项目位置"C:\Users\Liushiyi\IdeaProjects\pre1"

个人信息结构化数据存储在数据库边栏的data_collection_db@localhost下的data_collection_db下的表（Table）下的data_submissions

minio控制台：http://localhost:9090/browser/images
图像信息存储路径"D:\minio_data\images"

minio的启动：cmd中输入

cd D:\minio

D:

minio.exe server D:\minio_data --console-address ":9090"

运行时保证minio一直在运行状态，即不能关闭cmd

网页网址：http://localhost:8080/index.html（本机地址）

采用zeronews进行内网穿透，网址为https://il6szw40os.ny.takin.cc（去zeronews官网的映射处找到网址）

启动zeronews："D:\zeronews\zeronews.exe"右键exe用管理员模式打开，打开后输入zeronews.exe set token l50WseZ4hYHC3euF，成功后输入zeronews.exe start，保持窗口处在开启状态（和minio一样）

# 后端技术：

## 核心框架：Spring Boot

我们使用 Spring Boot 作为基础框架，它极大地简化了 Java Web 应用的开发，内置了 Tomcat 服务器，让我们能快速启动和运行一个独立的服务。

## 编程语言：Java

## API 接口层：Spring Web (MVC)

我们通过 @RestController 和 @PostMapping 等注解，创建了 RESTful API 接口，用来接收前端发来的数据和文件。

## 数据库持久层：Spring Data JPA & Hibernate

我们使用 Spring Data JPA 来操作数据库。它让我们能用非常简洁的 Java 代码（比如 repository.save()）来完成对数据库的增删改查，而无需手动编写复杂的 SQL 语句。Hibernate 是 JPA 的一个具体实现。

## 数据库：MySQL

我们选择并安装了 MySQL 数据库，用来存储像姓名、年龄、性别以及图片 URL 这样的结构化数据。

## 对象存储：MinIO

我们使用 MinIO 来存储用户上传的非结构化数据，也就是面相和舌象的图片文件。这是一种处理大量文件的标准做法。

## 项目构建与依赖管理：Apache Maven

我们使用 pom.xml 文件来管理项目的所有依赖库（比如 Spring Boot, MinIO客户端, MySQL驱动等），并负责项目的编译和打包。

# 前端技术：

## 基础结构：HTML5

我们使用标准的 HTML5 标签来构建网页的骨架，比如 form, input, select, video, canvas 等。

## 样式与布局：Tailwind CSS

为了快速获得一个美观、响应式的界面，我们的前端页面通过 CDN 引入了 Tailwind CSS 框架。它让我们能用实用工具类（Utility Classes）来直接在 HTML 中写样式。

## 核心交互逻辑：原生 JavaScript (ES6+)

我们使用现代 JavaScript (ES6+) 来实现所有的前端动态功能，没有依赖任何重型框架（如 Vue 或 React），这让项目保持轻量。主要功能包括：

### 摄像头访问：通过 navigator.mediaDevices.getUserMedia API 调用电脑摄像头。

### 拍照与预览：利用 <canvas> 元素绘制摄像头画面，实现拍照和预览。

### 异步数据提交：通过 fetch API 和 FormData 对象，将文本数据和图片文件异步地以 POST 请求发送到我们的后端服务器。

### DOM 操作：动态地更新页面元素，向用户显示“提交成功”或“失败”的反馈信息。

总的来说，我们构建的是一个采用了前后端分离架构的现代化 Web 应用。后端负责提供纯粹的数据接口，前端负责用户体验和数据采集，两者通过 HTTP API 进行通信。
