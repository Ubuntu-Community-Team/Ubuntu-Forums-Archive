---
title: "guvcview crashes: lubuntu 14.10 not working with laptop webcam"
date: 2015-02-15
forum: Multimedia Software
---

### Post by buzlite on 2015-02-15
I cannot get my laptop's built-in webcam to work with guvcview. Running this program results in a segmentation fault.  Could someone take a look at the below console output and give some insight.
Thanks in advance.

$ uname -a
Linux zzz 3.16.0-30-generic #40-Ubuntu SMP Mon Jan 12 22:06:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

$ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.5 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 6 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
09:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter

$ lsusb
Bus 001 Device 004: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


$ guvcview
guvcview 1.7.3
file guvcview_video.mkv has extension type 1
file guvcview_image.jpg has extension type 0

** (guvcview:6149): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
file guvcview_image.jpg has extension type 0
Video file suffix detected: 0
Image file suffix detected: 0
ALSA lib pcm_dsnoop.c:618:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video0 
vid:0bda 
pid:5776 
driver:uvcvideo
device doesn't seem to support uvc H264 (0)
Init. HP Truevision HD (location: usb-0000:00:1d.0-1.5)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/10, 
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/30, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/30, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/30, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/30, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 720 }
	Time interval between frame: 1/30, 
checking muxed H264 format support
device doesn't seem to support uvc H264 (0)
checking format: MJPG
VIDIOC_G_COMP:: Inappropriate ioctl for device
fps is set to 1/30
drawing controls

Segmentation fault (core dumped)

---

### Post by buzlite on 2015-02-15
As an update.
This other post could be related.
[http://ubuntuforums.org/showthread.php?t=2251286](http://ubuntuforums.org/showthread.php?t=2251286)

---

### Post by buzlite on 2015-02-15
The link specified in the previous post refers to a potential fix...[https://launchpad.net/~pj-assis/+archive/ubuntu/ppa](https://launchpad.net/~pj-assis/+archive/ubuntu/ppa)

---

