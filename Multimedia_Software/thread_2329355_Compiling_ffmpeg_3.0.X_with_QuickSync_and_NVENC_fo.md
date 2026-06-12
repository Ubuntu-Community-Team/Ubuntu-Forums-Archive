---
title: "Compiling ffmpeg 3.0.X with QuickSync and NVENC for ubuntu 16.04LTS"
date: 2016-06-30
forum: Multimedia Software
---

### Post by egandt on 2016-06-30
Getting this to work and working out how to do so given the mess that is 16.04LTS support for these features took a great deal of time, however I have instructions now that hopefully will assist others that want accelerated encoding support via ffmpeg.  I will not promise I did not miss anything, but it is many times better than you will find anywhere else on the web, and I will attempt to assist it you reply as well as  PM me.

```
ffmpeg with QucikSync and NVENC as well as most other major codecs for Ubuntu 16.04LTS

Install the basic graphics packages 
# apt-get install ffmpeg gxine libdvdread4 icedax tagtool libdvd-pkg easytag id3tool lame libxine2-ffmpeg nautilus-script-audio-convert libmad0 
mpg321 libavcodec-extra gstreamer1.0-libav mediainfo

Install other required packages for compiling ffmpeg:
# apt-get install autoconf automake m4 build-essential libass-dev libfreetype6-dev libsdl1.2-dev libtheora-dev libtool libva-dev libvdpau-dev libvorbis-dev libxcb1-dev libxcb-shm0-dev libxcb-xfixes0-dev pkg-config texinfo zlib1g-dev
# apt-get install yasm libx264-dev libmp3lame-dev libopus-dev libx265-dev libfdk-aac-dev libmp3lame-dev  libsdl1.2-dev libtheora-dev libtool libva-dev libvdpau-dev libvorbis-dev libvpx-dev libx264-dev libxcb1-dev libxcb-shm0-dev mercurial texinfo zlib1g-dev autoconf automake build-essential cmake libass-dev libfreetype6-dev libbluray-bdj libfaac-dev librtmp-dev libssh-dev libssh-gcrypt-dev opencl-headers libwebp-dev libvdpau-va-gl1 libgpac-dev libgpac4 libpciaccess-dev libvo-aacenc-dev libopencore-amrnb-dev libopencore-amrwb-dev
# apt-get install -y rpm alien libnuma1 pax intel-gpu-tools texi2html latex2html nvidia-modprobe nvidia-cuda-dev nvidia-cuda-toolkit libhugs-glut-bundled libmxu-dev freeglut3-dev libsctp1 libxi-dev lksctp-tools
# apt-get install nvidia-<XXX>
Where XXX is the driver release, as of writing this doc it was 361

Download and Install MediaInfo: https://sourceforge.net/p/mediainfo/activity/?page=0&limit=100#57751cd65fcbc941d9121a7c
    libmediainfo0v5_0.7.86-1_amd64.xUbuntu_16.04.deb
    mediainfo-gui_0.7.86-1_amd64.xUbuntu_16.04.deb
    mediainfo_0.7.86-1_amd64.xUbuntu_16.04.deb
# dpkg -i libmediainfo0v5_0.7.86-1_amd64.xUbuntu_16.04.deb mediainfo-gui_0.7.86-1_amd64.xUbuntu_16.04.deb mediainfo_0.7.86-1_amd64.xUbuntu_16.04.deb

Download the Nvidia video_sdk (6.0.1): http://developer.download.nvidia.com/assets/cuda/files/nvidia_video_sdk_6.0.1.zip
Optional download cuda from Nvidia for the Samples: http://developer.download.nvidia.com/compute/cuda/7.5/Prod/local_installers/cuda_7.5.18_linux.run

Download Intel Media Server Studio Essentials 2016: http://registrationcenter-download.intel.com/akdlm/irc_nas/8684/MediaServerStudioEssentials2016.tar.gz

Download: http://ftp.debian.org/debian/pool/main/l/lsb/
    lsb-invalid-mta_4.1+Debian13+nmu1_all.deb
    lsb-security_4.1+Debian13+nmu1_amd64.deb
    lsb-core_4.1+Debian13+nmu1_amd64.deb
# dpkg -i lsb-invalid-mta_4.1+Debian13+nmu1_all.deb lsb-security_4.1+Debian13+nmu1_amd64.deb lsb-core_4.1+Debian13+nmu1_amd64.deb

Checkout a copy of libmfx from github: git clone https://github.com/lu-zero/mfx_dispatch
# cd mfx_dispatch
# autoreconf -i
# ./configure --prefix=/usr/local --with-libva_drm --with-libva_x11 --enable-shared --enable-static
# make
# make install


Install and configure Intel Media Server Studio Essentials 2016:
# tar -xvzf MediaServerStudioEssentials2016.tar.gz
# cd MediaServerStudioEssentials2016
# tar -xvzf SDK2016Production16.4.4.tar.gz
# cd SDK2016Production16.4.4/Generic
Note: The shipping versions of va_drm and libva_x11 in ubuntu 16.04 are newer than those in the "Intel Media Server Studio Essentials 2016", so we will be using them.
# echo "/usr/local/lib" > /etc/ld.so.conf.d/libmfx.conf 
# echo "/opt/intel/common/mdf/lib64" > /etc/ld.so.conf.d/intel-mdf.conf
# echo "/opt/intel/opencl" > /etc/ld.so.conf.d/libintelopencl.conf
# chown -R root:root *
# cp -rdf opt/* /opt/
# cp -rdf etc/* /etc/
# cp -rdf usr/bin/*     /usr/local/bin/
# cp -rdf usr/include/* /usr/local/include/
# cp -rdf usr/share/*   /usr/local/share
# ln -s /opt/intel/opencl/include/CL /usr/local/include
# ldconfig
For every user that will use ffmpeg with qsv run:
# usermod -a -G video <user name>
# ldconfig -p | egrep "mfx|drm|libva"
You should see entries for mfx drm and libva
If yu want to test you will need the samples:
# git clone https://github.com/Intel-Media-SDK/samples
# cd samples/samples
# export MFX_HOME=/opt/intel/mediasdk
# perl build.pl --enable-drm=yes --enable-opencl=yes --cmake=intel64.make.debug --build
Test encoding works as this is what we need for ffmpeg
# ./__cmake/intel64.make.debug/__bin/debug/sample_multi_transcode -i::h_264 <some h264 file in> -o::h264 <file out>/h264 -hw
If this works then you are good to go with QuckSync


Next we need to configure Nvidia for nvenc encoding support:
The basic packages for NVENC support are already present above, however we still need a few changes to get compilation using it to work properly.
Download the Nvidia video_sdk (6.0.1): http://developer.download.nvidia.com/assets/cuda/files/nvidia_video_sdk_6.0.1.zip
Optional download cuda from Nvidia for the Samples: http://developer.download.nvidia.com/compute/cuda/7.5/Prod/local_installers/cuda_7.5.18_linux.run
# unzip nvidia_video_sdk_6.0.1.zip
# cd nvidia_video_sdk_6.0.1/Samples/common/inc
# cp * /usr/local/bin
Note the critical file is "nvEncodeAPI.h", however the others will also be useful.
# cd ../..
#  grep -r nvidia-352 -l --null . | xargs -0 sed -i 's#nvidia-352#nvidia-361#g
Replace 361 with the driver release number.
# make 
This will fail unable to location the library -lnvidia-encode to fix this we need to run:
# cd NvTranscoder
# g++ -m64 -O2 -o NvTranscoder NvTranscoder.o VideoEncoder.o FrameQueue.o VideoDecoder.o NvHWEncoder.o dynlink_cuda.o dynlink_nvcuvid.o -L/usr/lib/nvidia-361 -L/usr/lib64 -lnvidia-encode -ldl -lpthread
This will work, notice we need -L/usr/lib/nvidia-361 added as otherwise it can not find the lnvidia-encode, If your driver version is not 361 changes teh version as needed
At this point you can test NVENC encoding using NvEncoder
# cd NVEncoder
# ./NvEncoder -i ../common/video/plush1_720p_10s.m2v -o test.h264 -size 1920 1080 -codec 0
If this works then NVENC, should be functional as well


Finally onto ffmpeg:
Checkout a copy of ffmpeg from git
# git clone https://git.ffmpeg.org/ffmpeg.git ffmpeg-<version>
# cd ffmpeg-<version>
# export LDFLAGS=-L/usr/lib/nvidia-361
If your driver version is not 361 changes the version as needed
# ./configure  --enable-nonfree --enable-gpl --enable-version3  --enable-libmfx  --enable-cuda    --enable-nvenc  --enable-gcrypt --enable-avisynth  --enable-gcrypt  --enable-libass  --enable-libfaac  --enable-libfdk-aac --enable-libfontconfig --enable-libfreetype   --enable-libmp3lame  --enable-libopus  --enable-libpulse --enable-librtmp --enable-libssh  --enable-libtheora    --enable-libvorbis  --enable-libx264 --enable-libx265   --enable-opengl  --enable-openssl  --enable-libvpx --enable-libopencore-amrwb --enable-libopencore-amrnb --enable-libwebp --prefix=/<whgere you want the custom ffmpeg> --incdir=/opt/intel/mediasdk/include/mfx 
Do not overwrite the default ubuntu ffmpeg put this on is some other place say /usr/local
# make

Test ffmpeg using NVEVC, this assumes you have a test.mkv to test with
# ./ffmpeg -i test.mkv -c:v h264_nvenc -preset default output.mp4

Test ffmpeg using QuickSync, this assumes you have a test.mkv to test with
# ./ffmpeg -i test.mkv -c:v h264_qsv -preset:v faster output.mp4

Install the newly built ffmpeg
# make install


Assuming I did not forget anything or miss anything you should now have a custom ffmpeg with nvenc and quicksync support.

```

ERIC

---

### Post by Ilay on 2016-07-01
Hi Eric,

I'm trying to configure QuickSync support on 16.04 folowing your instructions.
The problem I'm facing is not working sample_multi_transcode, 

Here is the output.

```
test@ubuntu:~/qsv_test/distr/samples/samples&#10219; sudo MFX_HOME=/opt/intel/mediasdk ./__cmake/intel64.make.debug/__bin/debug/sample_multi_transcode -i::h264 vid.h264 -o::h264 transcoded.h264 -hw
Multi Transcoding Sample Version 0.0.000.0000

libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0

Return on error: error code -3, /home/vxg/qsv_test/distr/samples/samples/sample_multi_transcode/src/pipeline_transcode.cpp      2689


Return on error: error code -3, /home/vxg/qsv_test/distr/samples/samples/sample_multi_transcode/src/sample_multi_transcode.cpp  279


```

Any ideas?

Thanks,
Ilay.

---

### Post by egandt on 2016-07-02
what processor are you installing on?  I got this on a 3700K processor, because it it was not supported. (only 4, 5 and 6 series are supported, by Intel).

One thing I did notice is "Multi Transcoding Sample Version 0.0.000.0000" it should read: "Multi Transcoding Sample Version 6.0.xxx". not sure what would cause the version to be 0.0.000.0000 .

Lastly if you replace -hw with -sw does it work as then it should use the CPU, just wondering if you get the same failure.

looking at the code quickly, both fail on the same function "MSDK_CHECK_RESULT", which seem to be checking the input file for compatibility.

Sorry I can not point to just one thing, as you notice setting this up is a giant mess.

ERIC

---

### Post by h00re1337 on 2016-07-16
```
root@dell:~/samples/samples# vainfoerror: can't connect to X server!
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: User requested driver 'iHD'
libva info: Trying to open /opt/intel/mediasdk/lib64/iHD_drv_video.so
libva info: Found init function __vaDriverInit_0_32
Speicherzugriffsfehler (Speicherabzug geschrieben)
```

any idea? with ubuntu 14.04 with kernel 3.8 its works perfekt. its a xeon 1225 v3 with intel hd 4600.

---

### Post by egandt on 2016-07-16
I actually thought a 4.2+ kernel was required for QuickSync, from what I had read, but that there may be modules back ported to earlier kernels as well.  as for your error it looks like an X driver issue, off the top of my head, but that is not much to go off of.

ERIC

---

### Post by h00re1337 on 2016-07-17
```
root@dell:~/samples/samples# ./sys_analyzer_linux.py --------------------------
Hardware readiness checks:
--------------------------
** [ OK ] **Processor name: Intel(R) Xeon(R) CPU E3-1225 v3 @ 3.20GHz
--------------------------
OS readiness checks:
--------------------------
** [ ERROR ] **No compatible GPU available.  Check BIOS settings?
```

hm its crazy... no gpu available... in ubuntu 14.04 its working with the same server :/

---

### Post by mc4man on 2016-07-17
I think you should review your instructions, maybe missing a tar command or something - 
Install and configure Intel Media Server Studio Essentials 2016:
```
# tar -xvzf MediaServerStudioEssentials2016.tar.gz
# cd MediaServerStudioEssentials2016
# tar -xvzf SDK2016Production16.4.4.tar.gz
# cd MediaServerStudioEssentials2016
Note: The shipping versions of va_drm and libva_x11 in ubuntu 16.04 are newer than those in the "Intel Media Server Studio Essentials 2016", so we will be using them.
# echo "/usr/local/lib" > /etc/ld.so.conf.d/libmfx.conf 
# echo "/opt/intel/common/mdf/lib64" > /etc/ld.so.conf.d/intel-mdf.conf
# echo "/opt/intel/opencl" > /etc/ld.so.conf.d/libintelopencl.conf
# chown -R root:root *
[COLOR="#0000CD"]# cp -rdf opt/* /opt/
# cp -rdf etc/* /etc/
# cp -rdf usr/bin/*     /usr/local/bin/
# cp -rdf usr/include/* /usr/local/include/
# cp -rdf usr/share/*   /usr/local/share[/COLOR]
# ln -s /opt/intel/opencl/include/CL /usr/local/include
# ldconfig
```
The blue commands don't work here at the prompt you've reached previously ( /SDK2016Production16.4.4/Generic#,) with intel-linux-media-ocl_generic_16.4.4-47109_64bit.tar.gz still archived. ex. - 
/MediaServerStudioEssentials2016/SDK2016Production16.4.4/Generic# cp -rdf opt/* /opt/
cp: cannot stat 'opt/*': No such file or directory

---

### Post by egandt on 2016-07-17
cd to the generic directory and explode the tar.gz file then cd into that directory and execute the copies.

ERIC

---

### Post by h00re1337 on 2016-07-30
i try it again with i5-4570T and after reboot vainfo not works...

```
root@Lenovo:~# ./sys_analyzer_linux.py --------------------------
Hardware readiness checks:
--------------------------
** [ OK ] **Processor name: Intel(R) Core(TM) i5-4570T CPU @ 2.90GHz
--------------------------
OS readiness checks:
--------------------------
** [ OK ] **GPU visible to OS
--------------------------
Media Server Studio Install:
--------------------------
** [ OK ] **user in video group
** [ OK ] **libva.so.1 found
** [ ERROR ] **vainfo not reporting codec entry points
** [ ERROR ] **could not open /dev/dri/renderD128
--------------------------
Component Smoke Tests:
--------------------------
** [ OK ] **Media SDK HW API level:1.0
** [ OK ] **Media SDK SW API level:1.17
** [ OK ] **OpenCL check:NVIDIA: no NVIDIA devices found
platform:Intel(R) OpenCL GPU OK CPU OK


--------------------------
Media SDK Plugins available:
(for more info see /opt/intel/mediasdk/plugins/plugins.cfg)
--------------------------
    H264LA Encoder 	= 588f1185d47b42968dea377bb5d0dcb4
    VP8 Decoder 	= f622394d8d87452f878c51f2fc9b4131
```

then i try 

wget [http://www.wowza.com/downloads/WowzaTranscoder-4-Components/intel-quicksync-linux/intel-linux-media_ubuntu_16.3.2.22368_64bit.tar.gz](http://www.wowza.com/downloads/WowzaTranscoder-4-Components/intel-quicksync-linux/intel-linux-media_ubuntu_16.3.2.22368_64bit.tar.gz)
tar xvzf intel-linux-media_ubuntu_16.3.2.22368_64bit.tar.gz
[COLOR=#333333]cd intel-linux-media_ubuntu_16.3.2.22368_64bit[/COLOR][COLOR=#333333] 
[/COLOR][COLOR=#333333]./install_media[/COLOR][COLOR=#333333].sh [/COLOR]

reboot...then it works but it is an older mediasdk and not mediask 2016... there is everywhere a problem :/

---

### Post by be.cool on 2016-10-03
Hi, I tried to follow that tutorial to enable and build an enables Quick Sync Video FFMPEG but without much success.

Here is what I did to make it work:

I have a 6th gen core i3 which comes with Intel Quick Sync, so it is compatible with Media Server Studio Essentials 2017.

To get the system to work I used the following script from Intel's site:

```

#!/bin/bash


echo "remove other libdrm/libva"
find /usr -name "libdrm*" | xargs rm -rf
find /usr -name "libva*" | xargs rm -rf


echo "Remove old MSS install files ..."
rm -rf /opt/intel/mediasdk
rm -rf /opt/intel/common
rm -rf /opt/intel/opencl




echo "install user mode components"
#unpack the generic package
tar -xvzf intel-linux-media_generic*.tar.gz
tar -xvJf intel-opencl-16.5*.xz
tar -xvJf intel-opencl-devel-16.5*.xz


#put the generic components in standard locations


/bin/cp -r etc/* /etc
/bin/cp -r lib/* /lib
/bin/cp -r opt/* /opt
/bin/cp -r usr/* /usr


#ensure that new libraries can be found
echo '/usr/lib64' > /etc/ld.so.conf.d/libdrm_intel.conf
echo '/usr/local/lib' >> /etc/ld.so.conf.d/libdrm_intel.conf
ldconfig


echo "install kernel build dependencies"
apt-get -y install git fakeroot build-essential ncurses-dev xz-utils libssl-dev bc g++


echo "download 4.4 kernel"
if [ ! -f ./linux-4.4.tar.xz ]; then
     wget https://www.kernel.org/pub/linux/kernel/v4.x/linux-4.4.tar.xz
fi
tar -xJf linux-4.4.tar.xz


echo "apply kernel patches" 
cp  /opt/intel/mediasdk/opensource/patches/kmd/4.4/intel-kernel-patches.tar.bz2 .
tar -xvjf intel-kernel-patches.tar.bz2
cd linux-4.4
for i in ../intel-kernel-patches/*.patch; do patch -p1 < $i; done


echo "build patched 4.4 kernel" 
make olddefconfig
make -j 8
make modules_install
make install




echo "Install finished, please "
echo "1. update LD_LIBRARY_PATH to include /usr/lib64;/usr/local/lib"
echo "2. add user to video group: usermod -a -G video user"
echo "3. reboot"

```

This script installs the SDK and rebuilds the Kernel with several Intel's patchs. This step is crucial to get the Quick Sync Video do Work.

I installed the mfx_dispatch, using /usr prefix, in order to have MFX be identified by ffmpeg and other programs that use it.

Also, in order to proper make use of the tools I built with QSV support, I had to export some environment variables such as:
LIBVA_DRIVERS_PATH=/opt/intel/mediasdk/lib64

LIBVA_DRIVER_NAME=iHD 

LD_LIBRARY_PATH=/usr/lib64:/usr/local/lib

MFX_HOME=/opt/intel/mediasdk

Doing that I was able to make QSV work with TVHeadend, which as my main goal.
Also it is important to note that to make the tvheadend deamon to see enviroment variables I had to export them in the init.d script:

export LIBVA_DRIVERS_PATH=/opt/intel/mediasdk/lib64
export LIBVA_DRIVER_NAME=iHD

For building you should export PKG_CONFIG_PATH=/usr/lib64/pkgconfig:/usr/lib/pkgconfig to make pkg-config find the correct libs.

---

### Post by h00re1337 on 2016-10-21
Please Post your /etc/Environment. 

root@tvh1:~# /opt/intel/mediasdk/samples/sample_multi_transcode -i::h264 /opt/intel/mediasdk/samples/streams/test_stream.264 -o::h264 /home/test-stream-264
Multi Transcoding Sample Version 7.0.16053497

libva info: VA-API version 0.99.0
libva info: va_getDriverName() returns 0
libva info: User requested driver 'iHD'
libva info: Trying to open /opt/intel/mediasdk/lib64/iHD_drv_video.so
libva info: Found init function __vaDriverInit_0_32
libva info: va_openDriver() returns 0
Pipeline surfaces number (DecPool): 20
MFX HARDWARE Session 0 API ver 1.19 parameters:
Input  video: AVC
Output video: AVC

Session 0 was NOT joined with other sessions

Transcoding started
..
Transcoding finished

Common transcoding time is  0.06 sec
MFX session 0 transcoding PASSED:
Processing time: 0.06 sec
Number of processed frames: 101

The test PASSED

 

 

seems everything ok or?

 

root@tvh1:/home/jan# ./sys_analyzer_linux.py
--------------------------
Hardware readiness checks:
--------------------------
 [ OK ] Processor name: Intel(R) Core(TM) i7-6700K CPU @ 4.00GHz
--------------------------
OS readiness checks:
--------------------------
 [ OK ] GPU visible to OS
--------------------------
Intel(R) Media Server Studio Install:
--------------------------
 [ OK ] user in video group
 [ OK ] libva.so.1 found
 [ OK ] vainfo reports valid codec entry points
 [ ERROR ] could not open /dev/dri/renderD128

--------------------------
Media SDK Plugins available:
(for more info see /opt/intel/mediasdk/plugins/plugins.cfg)
--------------------------
    H264LA Encoder     = 588f1185d47b42968dea377bb5d0dcb4
    VP8 Decoder     = f622394d8d87452f878c51f2fc9b4131
    HEVC Decoder     = 33a61c0b4c27454ca8d85dde757c6f8e
    HEVC Encoder     = 6fadc791a0c2eb479ab6dcd5ea9da347
--------------------------
Component Smoke Tests:
--------------------------
 [ OK ] Media SDK HW API level:1.19
 [ OK ] Media SDK SW API level:1.19
 [ OK ] OpenCL check:platform:Intel(R) OpenCL GPU OK CPU OK

 

the compile from ffmpeg had an error...

./configure --enable-nonfree --enable-gpl --enable-libmfx --prefix=/home/ffmpeg --incdir=/opt/intel/mediasdk/include/mfx

make

/usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/libva-drm.a(va_drm.o): In Funktion `va_DisplayContextGetDriverName':
(.text+0xaa): Nicht definierter Verweis auf `drmGetMagic'
/usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/libva-drm.a(va_drm_auth.o): In Funktion `va_drm_is_authenticated':
(.text+0x6a): Nicht definierter Verweis auf `drmGetClient'
/usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/libva-drm.a(va_drm_auth.o): In Funktion `va_drm_authenticate':
(.text+0xf8): Nicht definierter Verweis auf `drmAuthMagic'
/usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/libva-drm.a(va_drm_utils.o): In Funktion `VA_DRM_GetDriverName':
(.text+0x2e): Nicht definierter Verweis auf `drmGetVersion'
/usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/libva-drm.a(va_drm_utils.o): In Funktion `VA_DRM_GetDriverName':
(.text+0x7d): Nicht definierter Verweis auf `drmFreeVersion'
/usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/libva-drm.a(va_drm_utils.o): In Funktion `VA_DRM_IsRenderNodeFd':
(.text+0x133): Nicht definierter Verweis auf `drmGetDeviceNameFromFd'
collect2: error: ld returned 1 exit status
Makefile:131: die Regel für Ziel „ffmpeg_g“ scheiterte
make: *** [ffmpeg_g] Fehler 1

---

### Post by hackeron on 2017-01-28
Anyone managed to get this working with the latest version? - Could you provide up to date instructions?

---

### Post by mc4man on 2017-01-28
> **hackeron said:**
> Anyone managed to get this working with the latest version? - Could you provide up to date instructions?nvenc can simply be enabled in any recent or current git master, ex.
$ ffmpeg -encoders |grep nvenc
ffmpeg version git-2017-01-22-7f9978b Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.4) 20160609
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libfreetype --enable-gnutls --disable-ffserver --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvidstab --enable-libtheora --enable-libwavpack --enable-libopenjpeg --enable-libgsm [COLOR="#0000CD"]--enable-nvenc[/COLOR]
  libavutil      55. 44.100 / 55. 44.100
  libavcodec     57. 75.100 / 57. 75.100
  libavformat    57. 63.100 / 57. 63.100
  libavdevice    57.  2.100 / 57.  2.100
  libavfilter     6. 69.100 /  6. 69.100
  libavresample   3.  2.  0 /  3.  2.  0
  libswscale      4.  3.101 /  4.  3.101
  libswresample   2.  4.100 /  2.  4.100
  libpostproc    54.  2.100 / 54.  2.100
 V..... h264_nvenc           NVIDIA NVENC H.264 encoder (codec h264)
 V..... nvenc                NVIDIA NVENC H.264 encoder (codec h264)
 V..... nvenc_h264           NVIDIA NVENC H.264 encoder (codec h264)
 V..... nvenc_hevc           NVIDIA NVENC hevc encoder (codec hevc)
 V..... hevc_nvenc           NVIDIA NVENC hevc encoder (codec hevc)

---

### Post by hackeron on 2017-01-29
I do not have an nvidia card :( - Anyone had any luck with QuickSync?

---

### Post by egandt on 2017-01-29
Compiling ffmpeg should be reasonable start forward I use the following:

#!/bin/bash
**export LDFLAGS=-L/usr/lib/nvidia-367**
./configure  --enable-nonfree --enable-gpl --enable-version3  --enable-libmfx  --enable-libnpp  **--enable-cuda    --enable-nvenc**  --enable-gcrypt --enable-avisynth  --enable-gcrypt  --enable-libass  --enable-libfdk-aac --enable-libfontconfig --enable-libfreetype   --enable-libmp3lame  --enable-libopus  --enable-libpulse --enable-librtmp --enable-libssh  --enable-libtheora    --enable-libvorbis  --enable-libx264 --enable-libx265  --enable-opengl  --enable-openssl  --enable-libvpx --enable-libopencore-amrwb --enable-libopencore-amrnb --enable-libwebp --prefix=/websites/emby_data/ffmpeg --incdir=/opt/intel/mediasdk/include/mfx --enable-opencl
make
make clean
make install

I just downloaded 3.2 from git and compiled it last week.  The key sections are in BOLD

ERIC

---

