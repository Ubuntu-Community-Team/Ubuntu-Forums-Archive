---
title: "eee PC - inbuilt Chicony webcam not working"
date: 2014-09-07
forum: Multimedia Software
---

### Post by fiooo on 2014-09-07
Hello, I installed Ubuntu on this netbook and I haven't been able to get the webcam to display any image.
Most threads I found while searching where from years ago with either dead links or solutions that don't work.

lsusb
```
04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
```

lsmod | grep uvc
```
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
```

Output of guvcview in terminal 
```
guvcview 1.7.1
file guvcview_video.mkv has extension type 1
file guvcview_image.jpg has extension type 0
file guvcview_image.jpg has extension type 0
Video file suffix detected: 0
Image file suffix detected: 0
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video0 
Init. CNF7129 (location: usb-0000:00:1d.3-2)
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 1/25, 
{ discrete: width = 1280, height = 1024 }
    Time interval between frame: 1/25, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/8, 
{ discrete: width = 1280, height = 1024 }
    Time interval between frame: 1/8, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 1/25, 
{ discrete: width = 1280, height = 1024 }
    Time interval between frame: 1/25, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/8, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 1/25, 
{ discrete: width = 1280, height = 1024 }
    Time interval between frame: 1/25, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/8, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 1/25, 
{ discrete: width = 1280, height = 1024 }
    Time interval between frame: 1/25, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/8, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 1/25, 
{ discrete: width = 1280, height = 1024 }
    Time interval between frame: 1/25, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/8, 
vid:04f2 
pid:b071 
driver:uvcvideo
checking format: 1196444237
VIDIOC_G_COMP:: Inappropriate ioctl for device
fps is set to 1/30
drawing controls

libv4l2: error turning on stream: Input/output error
VIDIOC_STREAMON - Unable to start capture: Input/output error
fps is set to 1/30
Checking video mode 320x240@32bpp : OK 
libv4l2: error turning on stream: Input/output error
VIDIOC_STREAMON - Unable to start capture: Input/output error
libv4l2: error turning on stream: Input/output error
VIDIOC_STREAMON - Unable to start capture: Input/output error


```
It detects the camera in the settings but no image.

Someone here said that he removed the drivers and reinstalled them to make it work, but I have no idea on how to do that.
[http://ubuntuforums.org/showthread.php?t=2186311](http://ubuntuforums.org/showthread.php?t=2186311)

Please let me know if there is any other information you need. 
Thank you

Edit:
Fixed it by disabling an re enabling the webcam in the BIOS (it was enabled under XP).

---

