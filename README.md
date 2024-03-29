# OpenCV_Install for Ubunutu-20.04 / Linux
OpenCV C++ Bash Script Install

```bash

 sudo apt-get install $(apt-cache --names-only search ^gstreamer1.0-* | awk '{print $1}' | grep -v gstreamer1.0-hybris | grep -v gstreamer1.0-python3-dbg-plugin-loader)

#sudo apt install build-essential cmake git pkg-config libgtk-3-dev \
#libavcodec-dev libavformat-dev libswscale-dev libv4l-dev \
#libxvidcore-dev libx264-dev libjpeg-dev libpng-dev libtiff-dev \
#gfortran openexr libatlas-base-dev python3-dev python3-numpy \
#libtbb2 libtbb-dev libdc1394-22-dev libopenexr-dev \
#libgstreamer-plugins-base1.0-dev libgstreamer1.0-dev \  


sudo apt install build-essential cmake git pkg-config libgtk-3-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libxvidcore-dev libx264-dev libjpeg-dev libpng-dev libtiff-dev  libatlas-base-dev libtbb2 libtbb-dev  libopenexr-dev  python3-dev python3-numpy libgstreamer-plugins-base1.0-dev libgstreamer1.0-dev -y


mkdir ~/opencv_build && cd ~/opencv_build 
git clone https://github.com/opencv/opencv.git 
git clone https://github.com/opencv/opencv_contrib.git 

cd ~/opencv_build/opencv && mkdir build && cd ~/opencv_build/opencv/build 


cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D INSTALL_C_EXAMPLES=ON \
-D WITH_OPENGL=ON \
-D WITH_TBB=ON \
-D WITH_GSTREAMER=ON \
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
-D BUILD_EXAMPLES=ON ..

make -j$(nproc)
sudo make install
pkg-config --cflags opencv4

```
