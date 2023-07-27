# Jetson_Setup_Guide

BSP Flash
BSP : https://s3.us-west-2.amazonaws.com/storage.avermedia.com/web_release_www/EN715/BSP/BSP-TX2+NX/EN715-TX2-NX-R1.0.4.4.6.tar.gz

sudo ./setup.sh
Select raspberry pi from options
power off -> press recovery button -> power on -> wait 2 seconds -> release recovery button
sudo ./install.sh


Change Root File System to SD Card directly 
https://www.forecr.io/blogs/bsp-development/change-root-file-system-to-sd-card-directly


CUDA installation
https://forums.developer.nvidia.com/t/manually-installing-cuda-11-0-2-on-jetson-xavier-nx-help/191909/6
sudo apt-get install nvidia-cuda

cuDNN installation
https://github.com/stereolabs/zed-tensorflow/issues/6 
sudo apt-get install libffi-dev
sudo apt-get install libcudnn8 libcudnn8-dev libcudnn8-samples -y

sudo apt-get install python-dev
sudo apt-get install build-essential autoconf libtool pkg-config python-opengl python-pil python-pyrex python-pyside.qtopengl idle-python2.7 qt4-dev-tools qt4-designer libqtgui4 libqtcore4 libqt4-xml libqt4-test libqt4-script libqt4-network libqt4-dbus python-qt4 python-qt4-gl libgle3 python-dev libssl-dev


Tensorrt Installation
https://forums.developer.nvidia.com/t/need-to-manually-install-tensorrt-on-nvidia-xavier-nx-board/213896/10

$ sudo echo "deb https://repo.download.nvidia.com/jetson/common r32.7 main" >> /etc/apt/sources.list.d/nvidia-l4t-apt-source.list 
$ sudo echo "deb https://repo.download.nvidia.com/jetson/t194 r32.7 main" >> /etc/apt/sources.list.d/nvidia-l4t-apt-source.list
$ sudo apt update 
$ sudo apt install nvidia-tensorrt


VPI installation
https://repo.download.nvidia.com/jetson/common/pool/main/libn/libnvvpi1/libnvvpi1_1.1.12_arm64.deb
sudo dpkg -i libnvvpi1_1.1.12_arm64.deb

sudo apt install nvidia-l4t-jetson-multimedia-api

error: command 'aarch64-linux-gnu-gcc' failed with exit status 1
sudo apt-get install --reinstall build-essential


OPENCV Installation
https://www.bojankomazec.com/2019/12/installing-opencv-4-on-nvidia-jetson.html
cmake command:
cmake -D CMAKE_BUILD_TYPE=RELEASE -D WITH_CUDA=ON -D CUDA_ARCH_PTX="" -D CUDA_ARCH_BIN="5.3,6.2,7.2" -D WITH_CUBLAS=ON -D WITH_LIBV4L=ON -D BUILD_opencv_python3=ON -D BUILD_opencv_python2=OFF -D BUILD_opencv_java=OFF -D WITH_GSTREAMER=OFF -D WITH_GTK=ON -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D BUILD_EXAMPLES=OFF -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-4.1.2/modules -D OPENCV_DNN_CUDA=ON -D WITH_CUDNN=ON -D WITH_LIBV4L=ON -DOPENCV_GENERATE_PKGCONFIG=YES ..


Setup Python Virtual Environment:
Python 3.6.9
https://www.liquidweb.com/kb/how-to-setup-a-python-virtual-environment-on-ubuntu-18-04/
Python 3.9
https://arcanesciencelab.wordpress.com/2021/02/14/building-python-3-9-1-on-jetpack-4-5-and-the-jetson-xavier-nx/


Install Yolov5 dependencies:
https://github.com/ultralytics/yolov5/issues/9627


Activate TRT in virtual environment
command: export PYTHONPATH=/usr/lib/python3.6/dist-packages:$PYTHONPATH


Pt to trt conversion
command: python export.py –weights[] –include[] –device[] –simplify –half


Runiing yolov5:
Add rtsp links in file named streams.txt
command: python yolov5_track.py –weight[] –source streams.txt  


Additional resource:
	https://www.forecr.io/blogs/bsp-development/change-root-file-system-to-sd-card-directly
https://github.com/ultralytics/yolov5/issues/9627
https://www.bojankomazec.com/2019/12/how-to-install-tensorrt-python-package.html
https://forums.developer.nvidia.com/t/how-to-check-the-jetpack-version/69549/12
https://tecadmin.net/how-to-switch-python-version-in-ubuntu-debian/
https://forums.developer.nvidia.com/t/troubles-installing-matplotlib-on-nano-with-python-3-7-3-8-and-a-virtual-env/166837/2
https://forums.developer.nvidia.com/t/tensorflow-for-jetson-tx2/64596
https://www.bojankomazec.com/2019/12/installing-opencv-4-on-nvidia-jetson.html

sudo ln -s /usr/include/opencv4/opencv2 /usr/include/opencv2
with linked, in ubuntu20.04, this problem can be solved.


Clear PIP cache: 
	sudo rm -ef `/.cache/pip
	rm -rf  ~/.cache/pip

Matplotlib install
  apt-get install python3.8-dev
  pip install --upgrade pip setuptools wheel  
  pip install numpy==1.19.4
  pip install matplotlib

  sudo apt-get install python-dev

sudo apt-get install build-essential autoconf libtool pkg-config python-opengl python-pil python-pyrex python-pyside.qtopengl idle-python2.7 qt4-dev-tools qt4-designer libqtgui4 libqtcore4 libqt4-xml libqt4-test libqt4-script libqt4-network libqt4-dbus python-qt4 python-qt4-gl libgle3 python-dev libssl-dev


YOLOV8: https://i7y.org/en/yolov8-on-jetson-nano/

https://forums.developer.nvidia.com/t/vs-code-can-t-launch-with-jetpack-5-0/213980

https://github.com/mdegans/nano_build_opencv

https://forums.developer.nvidia.com/t/can-not-install-onnx-1-4-1-on-jetson-tx2/173354/6d

pip install onnx>=1.10.0


Python3.9 tensorrt pybindings : https://forums.developer.nvidia.com/t/tensorrt-on-jetson-with-python-3-9/196131/5

Python pytorch building: https://i7y.org/en/building-jetson-nano-libraries-on-host-pc/

Python3.9 torch.whl: https://files.pythonhosted.org/packages/46/32/548df53b686b55edf47041b5435f74be272daf06ea1d671646e14172fe20/torch-1.8.0-cp39-cp39-manylinux2014_aarch64.whl

ONNSIM install : https://github.com/daquexian/onnx-simplifier/issues/222
ONNSIM install imp:https://github.com/daquexian/onnx-simplifier/issues/214

ONNXRUNTIME: https://onnxruntime.ai/docs/build/eps.html#nvidia-jetson-tx1tx2nanoxavier

$ sudo apt update
$ sudo apt install python3-pip
$ sudo pip3 install -U jetson-stats



