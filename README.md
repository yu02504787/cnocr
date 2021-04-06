## 本项目基于[chineseocr_lite](https://github.com/opweiyi/chineseocr_lite)  实现中文自然场景图像的文字检测及识别


## Bash 运行 在项目根目录下运行 自定义端口.如:8000
``` Bash
python app.py 8000
```


## Docker 运行
- 重写Dockerfile，资源占用更小，可在1C 1G的学生服务器编译成功
- 编译生成镜像
docker build -t ocr .
- web app运行到容器
``` Bash
docker run --name ocr_ui -p8000:8000 -d ocr python3 app.py 8000
```


## web 访问服务
http://127.0.0.1:8000/ocr


## RESTful API demo
post /ocr
host 127.0.0.1:8000

{
"ImgString":"data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAcAAAAHCAYAAADEUlfTAAAAMUlEQVQYV2P8////fwYcgBFZkpGRkQFZLVgSJIgOQIrgkmAOVCecJqgTZiRWO3G5FgA9bTDs12fziwAAAABJRU5ErkJggg=="
,"textLine":false
}

- 请求url: http://127.0.0.1:8000/ocr
- 请求方式：POST
- 请求参数
    - ImgString：图片转base64后的字符串
    - textLine: 单行文字 true 

- 返回实例

{"res": [{"text": "\u4e2d", "name": "0", "box": [0, 0, 7, 0, 7, 7, 0, 7]}], "timeTake": 0.01}

- timeTake 0.01 s
