---
title: "Yet another issue with a logitech built-in webcam"
date: 2012-09-25
forum: Multimedia Software
---

### Post by cheluna on 2012-09-25
Hello!!

I have a problem with my built-in webcam. It used to be work, but around a  year ago, it stopped working. I use Ubuntu 10.04 so I waited for the new LTS Ubuntu Release  to see if that version could fix my problem, but I couldn't install it (I mean, I could, but I got that awful black screen issue).
So I came back to My Ubuntu Lucid Version, but it still does not work.
I does not work in Cheese, guvcview, gmail or skype. Not working at all. I  get a black screen and the light of the webcam does not switch on.
I've tried attaching an external webcam (Creative) and even if the light turned on, I still got the black screen. 

Don't have a clue.

Here are the things you'll probably ask:
```
lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0402:9665 ALi Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
lsmod | grep videodev
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
```If I run guvcview from the terminal, I got this:
```
guvcview 1.1.3
bt_audio_service_open: connect() failed: Conexión rehusada (111)
bt_audio_service_open: connect() failed: Conexión rehusada (111)
bt_audio_service_open: connect() failed: Conexión rehusada (111)
bt_audio_service_open: connect() failed: Conexión rehusada (111)
video device: /dev/video0 
/dev/video0 - device 1
Init. 1.3M WebCam (location: usb-0000:00:1d.7-4)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 2/15, 
{ discrete: width = 1280, height = 1024 }
    Time interval between frame: 2/15, 
checking format: 1448695129
vid:0402 
pid:9665 
driver:uvcvideo
 Could not grab image (select timeout): Recurso no disponible temporalmente
write /home/consuelo/.guvcviewrc OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
```However, another time, when I run guvcview, between the code, it appeared this:

```
VIDIOC_S_FORMAT - Unable to set format: Device or resource busy
Init v4L2 failed !! 
ERROR: Minimum Setup Failed.
 Exiting...
Terminated.
```I hope this is useful!! 

Thank you all!!

---

### Post by cheluna on 2012-09-26
Oh, nobody knows? please!!

---

### Post by mörgæs on 2012-09-26
I would begin with a fresh install of one of the 12.04 releases. Xubuntu is a good candidate if you have problems with Ubuntu. 

Better to invest some time in getting 12.04 to run than wrestling an obsolete version of Guvcview.

---

### Post by cheluna on 2012-09-26
But I got that black screen issue... I don't know how to deal with it. I've tried a lot of new linux version (ubuntu 12.04, linux mint, debian) and I got that black screen... :(

---

### Post by mörgæs on 2012-09-27
I see you have opened a new thread on the topic. As we don't like double-posting I'll close this one. Please don't double-post or bump in the future.

You have still not told which hardware you are dealing with and how you tried to install. Did you try the alternate installer, for example?

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Good luck.

---

