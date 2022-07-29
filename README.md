# YOLO v7 on Google Colaboratory

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/husty530/Yamashita-yolov7/blob/master/YOLOv7-Training.ipynb)

当リポジトリではLinux環境(Google Colab)でのビルドを想定して、簡単にセットアップができるようにPyTorchのYOLOv7ソースコードを配置しています。  
ブラウザさえあれば誰でも動かせますので、以下の手順でやってみましょう。  
本家を触りたい方は[こちら](https://github.com/WongKinYiu/yolov7)へ。

## つかいかた  
1. [YOLOv7-Training.ipynb](/YOLOv7-Training.ipynb)をGoogle Colaboratoryで開きます。ipynbはDriveに置くでも上のバッジから開くでもいいです。
2. ランタイムのタイプを"GPU"に変更し、本リポジトリをDriveに置きます。手動でもいいですが，ドライブをマウントしたあとでipynbの先頭に以下を打ち込むと早いです。
```
%cd /content/drive/MyDrive
!git clone https://github.com/husty530/Yamashita-yolov7.git
```
3. [workspace](/workspace)内にフォルダを作り、[pumpkin_640_480/dataset](/workspace/pumpkin_640_480/dataset)を参考に画像とラベルのフォルダを作ります。対応する画像とラベルの名前は必ず同じにしてください。
4. 他にも設定してね風味のあるところでは，適宜クラス数や画像サイズなどを適切に指定してください。
5. 上からポチポチしていきます。学習開始して、ザーッと画面が流れ始めたら成功です。
6. 終わったら、モデルを使って評価実行してみましょう。自分のフォルダに生成された"モデル名.pt"が最終成果物です。

.pt, .onnx 形式での保存ができるので、ダウンロードすればローカルでモデルを使用できます。PyTorchは付属のDemoプログラムのようなもので動きます。 
私のリポジトリ[Husty-public](https://github.com/husty530/Husty-public) ではC#のONNX Runtime経由でOpenCvSharpと連結したものを公開しています。

### ラベリング
正解ラベル付けはColabでなくローカル環境で行います。  
データフォーマットは物体一つにつきスペース区切りで(index) (x) (y) (width) (height)\nです。ただし、すべて画像の幅高さで割って0~1に丸めたものとなります。
ただのテキストファイルなので自作もできますが、[labelImg](https://github.com/tzutalin/labelImg)というフリーソフトが便利なのでそれを使いましょう。  
Python環境があるなら、pipコマンドが使える環境で
```
pip install labelImg
labelImg
```
だけで起動OK。 
