---
title: "Webcam Configuration On Kubuntu 10.10"
date: 2011-02-06
forum: Multimedia Software
---

### Post by MODYSAMA on 2011-02-06
Hello,
I am a linux beginner and need your cooperation,

**_[COLOR="Blue"]Operating system:[/COLOR]_**
Kubuntu 10.10
Kernel 2.6.35-22 Generic
My laptop is HP probook 4520s 

**_[COLOR="blue"]Webcam information:[/COLOR]_**
Name: FaceCam 312
Brand: Genius
Output: MJPG
Frame rate: Up to 30fps
Interface: USB
Plug and play. Driveless

**_[COLOR="blue"]The problem:[/COLOR]_**
Webcam work **only** on guvcview in **only** resolutions:
170*144
160*120

[COLOR="DarkGreen"]Cheese:[/COLOR]
> sok@sok-HP-ProBook-4520s:~$ cheese
libv4l2: error turning on stream: No space left on device
[COLOR="DarkGreen"]Ekiga:[/COLOR]
> sok@sok-HP-ProBook-4520s:~$ ekiga
libv4l2: error turning on stream: No space left on device
libv4l2: error reading: Invalid argument

[COLOR="DarkGreen"]Gsreamer-properties[/COLOR]
> sok@sok-HP-ProBook-4520s:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'alsasink'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'alsasrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video1'. [gstv4l2object.c(1983): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: Input/output error]

[COLOR="DarkGreen"]lsusb:[/COLOR]
> sok@sok-HP-ProBook-4520s:~$ lsusb
**Bus 002 Device 003: ID 0458:7076 KYE Systems Corp. (Mouse Systems) **
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05c8:0403 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 003: ID 03f0:231d Hewlett-Packard 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[COLOR="DarkGreen"]dmesg[/COLOR]
[HTML]> sok@sok-HP-ProBook-4520s:~$ dmesg | grep usb
[    1.023883] usbcore: registered new interface driver usbfs
[    1.023892] usbcore: registered new interface driver hub
[    1.023914] usbcore: registered new device driver usb
[    1.470341] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.717079] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.920759] usb 1-1.1: new full speed USB device using ehci_hcd and address 3
[    2.092428] usb 1-1.5: new high speed USB device using ehci_hcd and address 4
[   19.949461] usbcore: registered new interface driver btusb
[   19.949741] input: HP Webcam [2 MP Fixed] as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input7
[   19.949802] usbcore: registered new interface driver uvcvideo
[ 6286.153851] usb 2-1.1: new full speed USB device using ehci_hcd and address 3
[ 6286.390847] input: FaceCam 312 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input11
[ 6286.451123] usbcore: registered new interface driver snd-usb-audio
sok@sok-HP-ProBook-4520s:~$ 
[/HTML]

[CENTER][FONT="Georgia"]I tried [COLOR="Red"]that webcam[/COLOR] on another laptop same version of ubuntu and same kernel (mini HP laptop), webcam worked out of box in all softwares with all supported resolutions.[/FONT]

Actually, I have published that problem in several sites and that what I reach withit's helping.[/CENTER]

---

### Post by no2498 on 2011-02-06
try unpluging the cam restart the computer

plug in the cam retry the programs it did not work in
try skype last
looks as a program did not turn off right

---

### Post by MODYSAMA on 2011-02-08
Hello,
I tried it still the problem.
Actually the problem is still about month ago.
Is there any help, please?

---

### Post by no2498 on 2011-02-09
only thing i can think of is is the program xawtv
it loads a grabber
its in the package manager
after installed look in sound and video for it

---

### Post by MODYSAMA on 2011-02-09
It open the integrated hp camera not the usb webcama and get that:
```
sok@sok-HP-ProBook-4520s:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.35-25-generic)
xinerama 0: 1366x768+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x1 [PAL_B]): Invalid argument
config: invalid value for norm: (null)
valid choices for "norm": 
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
```

---

### Post by MODYSAMA on 2011-02-09
Is there anything missed any my HP laptop?
```

sok@sok-HP-ProBook-4520s:~$ dmesg | tail
[ 9014.027823] **HP WMI: Unknown response received**
[11532.813381] usb 2-1.1: new full speed USB device using ehci_hcd and address 3
[11533.036563] uvcvideo: Found UVC 1.00 device FaceCam 312 (0458:7076)
[11533.036570] uvcvideo: Forcing device quirks to 0x80 by module parameter for testing purpose.
[11533.036576] uvcvideo: Please report required quirks to the linux-uvc-devel mailing list.
[11533.051169] input: FaceCam 312 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input12
[11533.386733] usbcore: registered new interface driver snd-usb-audio
[14869.857110] **HP WMI: Unknown response received**
[15692.956427] show_signal_msg: 9 callbacks suppressed
[15692.956437] xawtv.bin[29033]: segfault at 0 ip 0106d770 sp bfe12bf8 error 4 in libc-2.12.1.so[ff9000+157000]
```
I can't understand that error?

---

### Post by MODYSAMA on 2011-02-14
please I am in need to help 
any ides any suggestions please

---

### Post by no2498 on 2011-02-15
type this in a terminal gstreamer-properties click enter
click video
you can change cam names
do the bottom test button

---

### Post by MODYSAMA on 2011-02-15
Thanks for replying, sir.
```
sok@sok-HP-ProBook-4520s:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'alsasink'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'alsasrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video1'. [gstv4l2object.c(1983): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: Input/output error]

```

---

### Post by MODYSAMA on 2011-02-15
no2498,
Excuse me, sir:
you have seen my post on linuxquestions I put extra information, you can have a look on . May be its provide you for helping me.

---

