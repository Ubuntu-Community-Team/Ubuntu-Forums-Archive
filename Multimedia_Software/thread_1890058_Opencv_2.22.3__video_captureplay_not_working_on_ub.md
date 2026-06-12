---
title: "Opencv 2.2/2.3  video capture/play not working on ubuntu 10.10"
date: 2011-12-02
forum: Multimedia Software
---

### Post by RobDaNet on 2011-12-02
Hi all
I spent the last few days trying to install Opencv in Ubuntu 10.10. Everything went well except for the video capture and reproduction facilities. I tried the following Opencv versions :
 2.2 + ffmpeg 0.7 , downloaded(tar) ,compiled and installed (video/capture not OK)
 2.1 installed with ubuntu software center(video/capture OK) 
 2.2 downloaded(tar) ,compiled and installed (video/capture not OK)
 2.3.1 + ffmpeg 0.8.5 downloaded(tar) ,compiled and installed (video/capture not OK)
 I hate to think that the new modular c++ opencv may not work on ubuntu 10.10 which I love so please at least tell me that someone has managed to install the new version(>=2.2).
This is the script I used to automate the installation and all the configuration :
```
#Installing dependencies
sudo apt-get install g++ build-essential libgtk2.0-dev libjpeg62-dev libtiff4-dev libjasper-dev libopenexr-dev cmake python-dev python-numpy libtbb-dev libeigen2-dev yasm libfaac-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev

#Downloading, compiling and installing ffmpeg
cd ~
mkdir opencv
cd opencv
mkdir ffmpeg
cd ffmpeg
wget -Nc http://ffmpeg.org/releases/ffmpeg-0.7-rc1.tar.gz
tar -xvzf ffmpeg-0.7-rc1.tar.gz
cd ffmpeg-0.7-rc1
./configure --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libxvid --enable-x11grab --enable-swscale --enable-shared
make
sudo make install

#Downloading, compiling and installing opencv
cd ~
cd opencv
mkdir opencv2.2
cd opencv2.2
wget -Nc http://downloads.sourceforge.net/project/opencvlibrary/opencv-unix/2.2/OpenCV-2.2.0.tar.bz2
tar -xvf OpenCV-2.2.0.tar.bz2
cd OpenCV-2.2.0/
cmake -D WITH_TBB=ON -D BUILD_NEW_PYTHON_SUPPORT=ON -D WITH_V4L=OFF -D INSTALL_C_EXAMPLES=ON -D INSTALL_PYTHON_EXAMPLES=ON -D BUILD_EXAMPLES=ON .
make
sudo make install

#Additional configurations
echo /usr/local/lib | sudo tee -a /etc/ld.so.conf.d/opencv.conf
sudo ldconfig
echo 'PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig' | sudo tee -a /etc/bash.bashrc
echo 'export PKG_CONFIG_PATH' | sudo tee -a /etc/bash.bashrc
sudo cp /usr/local/lib/python2.6/site-packages/cv.so /usr/local/lib/python2.6/dist-packages/
clear
echo 'Reboot your computer'
```Thanks.

---

### Post by no2498 on 2011-12-03
see if this helps it loads a cam grabber for my computers
open a terminal type dmesg click enter
after it stops click close
retry your cam in the program you use

---

### Post by RobDaNet on 2011-12-03
Thanks for answering no2498. I followed your advice but unfortunately no luck. I wrote in a file dmesg output and checked the relevant lines, and everything seems normal. The most irritating thing of all it is the fact that when I run an opencv program the led on my web cam lights up but the window with the image doesn't show out. Also the capture method woks fine in openframeworks and in Processing and  in opencv 2.1, like I said before.

---

