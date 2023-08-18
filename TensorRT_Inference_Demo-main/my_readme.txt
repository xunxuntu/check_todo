


# 先导出  onnx 模型
python export.py --weights=yolov5s.pt  --dynamic --simplify --include=onnx --opset 11

# 在导出 trt 模型
root@rtx2060:/usr/local/TensorRT-8.4.3.1/bin# ./trtexec --onnx=/home/tuc/yolov5-6.1/weights/yolov5s.onnx --saveEngine=/home/tuc/yolov5-6.1/weights/outfpbest.trt --workspace=2048 --best

# 运行
root@rtx2060:/home/tuc/TensorRT_Inference_Demo-main/bin# ./object_detection yolov5 /home/tuc/yolov5-6.1/data/images


20230816：将 dynamic 设为0后，运行命令后产生的推理图片没有画框。
20230817: 重新编译后还是如此。
