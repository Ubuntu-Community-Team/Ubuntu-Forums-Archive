---
title: "streaming from logitech quickcam"
date: 2011-06-09
forum: Multimedia Software
---

### Post by deadtom on 2011-06-09
What I'm trying to do is set up my quickcam to stream video to a web page for zone minder to pick up. If that makes any sense.

Here is the error that I'm getting:

```
libavutil 50.15. 1 / 50.15. 1
libavcodec 52.72. 2 / 52.72. 2
libavformat 52.64. 2 / 52.64. 2
libavdevice 52. 2. 0 / 52. 2. 0
libavfilter 1.19. 0 / 1.19. 0
libswscale 0.11. 0 / 0.11. 0
libpostproc 51. 2. 0 / 51. 2. 0
[video4linux2 @ 0x22a1640]Cannot find a proper format for codec_id 0, pix_fmt -1.
/dev/video0: Input/output error
```I've got ffserver running with this config, which I'm not entirely sure of:

```
Port 8090
# bind to all IPs aliased or not
BindAddress 0.0.0.0
# max number of simultaneous clients
MaxClients 1000
# max bandwidth per-client (kb/s)
MaxBandwidth 10000
# Suppress that if you want to launch ffserver as a daemon.
NoDaemon

<Feed feed1.ffm>
File /tmp/feed1.ffm
FileMaxSize 5M
</Feed>

<Stream webcam.mjpeg>
Feed feed1.ffm
Format mpjpeg
VideoSize qvga
VideoFrameRate 2
VideoIntraOnly
Noaudio
Strict -1
</Stream>

```Here is the ffmpeg command that I'm using:

*ffmpeg -r 15 -s 352x288 -f video4linux2 -i /dev/video0 [http://localhost:8090/feed1.ffm](http://localhost:8090/feed1.ffm)*

v4l-info output:
```
### v4l2 device info [/dev/video0] ###
general info
VIDIOC_QUERYCAP
driver : "tv8532"
card : "USB Camera (046d:0920)"
bus_info : "usb-0000:00:1d.2-1"
version : 2.9.0
capabilities : 0x5000001 [VIDEO_CAPTURE,READWRITE,STREAMING]

standards

inputs
VIDIOC_ENUMINPUT(0)
index : 0
name : "tv8532"
type : CAMERA
audioset : 0
tuner : 0
std : 0x0 []
status : 0x0 []

video capture
VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
index : 0
type : VIDEO_CAPTURE
flags : 0
description : "BA81"
pixelformat : 0x31384142 [BA81]
VIDIOC_G_FMT(VIDEO_CAPTURE)
type : VIDEO_CAPTURE
fmt.pix.width : 352
fmt.pix.height : 288
fmt.pix.pixelformat : 0x31384142 [BA81]
fmt.pix.field : NONE
fmt.pix.bytesperline : 352
fmt.pix.sizeimage : 101376
fmt.pix.colorspace : SRGB
fmt.pix.priv : 0

controls
VIDIOC_QUERYCTRL(BASE+0)
id : 9963776
type : INTEGER
name : "Brightness"
minimum : 1
maximum : 351
step : 1
default_value : 332
flags : 0

### video4linux device info [/dev/video0] ###
general info
VIDIOCGCAP
name : "USB Camera (046d:0920)"
type : 0x1 [CAPTURE]
channels : 1
audios : 0
maxwidth : 352
maxheight : 288
minwidth : 48
minheight : 32

channels
VIDIOCGCHAN(0)
channel : 0
name : "tv8532"
tuners : 0
flags : 0x0 []
type : CAMERA
norm : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
VIDIOCGAUDIO
audio : 0
volume : 0
bass : 0
treble : 0

picture
VIDIOCGPICT
brightness : 61977
hue : 0
colour : 0
contrast : 0
whiteness : 0
depth : 8
palette : unknown

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
VIDIOCGWIN
x : 0
y : 0
width : 352
height : 288
chromakey : 0
flags : 0

```output of dmesg | grep video:
```

[ 0.687315] pci 0000:00:02.0: Boot video device
[ 27.448814] Linux video capture interface: v2.00
[ 27.842707] gspca: video0 created

```I'm sure I'm doing something wrong here. Any help is greatly appreciated.

---

### Post by deadtom on 2011-06-13
-bump-

Anyone?

---

### Post by ajithabraham.m on 2011-06-19
hi
try this command 

ffmpeg -r 15 -s 352x288 -f video4linux2 -i /dev/video0 -f flv  [http://localhost:8090/feed1.ffm](http://localhost:8090/feed1.ffm)
 now the encode will start

but i had a problem when i connect to ffserver with a player it connect but can't get video do u have any idea about that configuration is same as the above

---

