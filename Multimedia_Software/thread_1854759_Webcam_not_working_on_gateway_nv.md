---
title: "Webcam not working on gateway nv"
date: 2011-10-05
forum: Multimedia Software
---

### Post by bholzer on 2011-10-05
Just got skype, and noticed my webcam wouldn't work. So I installed cheese and tried to use it, but nothing happens. I looked through my /dev/ directory and saw no video there. Any body have advice?

---

### Post by no2498 on 2011-10-05
look in your system startup programs make sure skype and cheese are not set to run at startup
if 1 was set to run turn it off and restart the computer
after that
in a terminal type dmesg click enter
after it stops type lsusb click enter

try the cam in cheese

---

### Post by jmacwill on 2011-10-05
I had the exact same issue with my HP mini 110, running 11.04

I did as you said, and it worked perfectly!  Thanks so much!

But I have a question:  what exactly did I do by making those two entries?

Second:  where do I find the start-up files?  It is not clear as to where I would find them.

Thanks

Jonathan

---

### Post by no2498 on 2011-10-06
ive seen dmesg load a cam grabber on my computer
look in your system,preference,startup applications
i only say this because windows has its hand in skype now
in turn cheese or skype will not start up
lsusb is only to see what cam you have in case you need a driver
glad it helped you

---

### Post by bholzer on 2011-10-06
I am not sitting at the right computer at the moment, but I remember running lsusb a while back and getting some weird results. I am almost certain I will need a driver. I'll post the results of lsusb from the correct computer when I get a chance.

---

### Post by no2498 on 2011-10-07
if it comes up as a rico cam you do need a driver

---

### Post by bholzer on 2011-10-17
Just got back to this, sorry for the delay. lsusb gives me weird output:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Saw this in the dmesg output, however :

[22468.380276] uvcvideo: Found UVC 1.00 device Video WebCam (064e:a103)
[22468.397067] input: Video WebCam as /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/input/input8
[22469.266996] usb 2-5: USB disconnect, device number 5
[22469.524234] usb 2-5: new high speed USB device number 6 using ehci_hcd
[22469.699122] uvcvideo: Found UVC 1.00 device Video WebCam (064e:a103)
[22469.716122] input: Video WebCam as /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/input/input9

---

### Post by no2498 on 2011-10-17
install guvcview try the cam in it

---

### Post by bholzer on 2011-10-17
It gave me the error:
Unable to open device.

I opened it in terminal, this is the output:

ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
)
ALSA lib audio/pcm_bluetooth.c:1613: (audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613: (audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957: (snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018: (snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
unable to detect video devices on your system (0)
ERROR opening V4L interface: No such file or directory
Init video returned -1

---

### Post by no2498 on 2011-10-19
if your on a laptop you may need to click the fn+f4 keys to turn the cam on first

---

### Post by bholzer on 2011-10-19
AH! That worked the first time, but then after I closed cheese, it stopped. 

I don't understand!:-k

---

### Post by nightshadowfx on 2011-10-19
when I was running ubuntu 11.04 my webcam work on my acer netbook and on my friends acer laptop but since I updated both computers to 11.10 every time I try and use the webcam on chat it gives me an error.

---

### Post by no2498 on 2011-10-20
this may or may not help
open a terminal
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
this is for 32 bit only
click enter

---

