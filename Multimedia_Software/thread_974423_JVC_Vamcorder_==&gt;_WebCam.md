---
title: "JVC Vamcorder ==&gt; WebCam ?"
date: 2008-11-07
forum: Multimedia Software
---

### Post by nedmar on 2008-11-07
Hi all,

I have a JVC GR-E340E camcorder wich i succesfully used as webcam on WindowsXP for almost 2 years now.
Didn't had any success trying the same on Ububtu.

The Camera can be used very easy to capture video and audio( from already registered tapes or direct capture on the PC ) with Kino, so no problem with the system detecting it..

output from
```
~$ ls /dev/raw1394 
/dev/raw1394
~$ ls /dev/dv1394/
0
```

The chat programs i've tryed are Skype and Ekiga.After searching the web almost an hour i found out there is no support for Firewire/IEEE1394 in Skype and there is also no intention to include this option.
It remained Ekiga.. it has no problem detecting the camera, but it stucks to "standby" when i press the webcam start button ( using videoplugin 1394AVC witch detects as input the camcorder type and model ) and it's completelly crashes when i use videoplugin 1394DC witch detects as input device "  /dev/raw1394  " ( previously chmod 777 /dev/raw1394 - Kino requiered)

Quetions:
1. Is there any yahoo/skype Chat system for linux that supports Video including from IEEE1394 devices?If Yes, please post link.
2. Is there any software(e.g.[splitcam]("http://splitcamera.com") or [Camtasia Studio ]("http://www.techsmith.com/camtasia.asp")(not free) )  for linux able to connect several applications using a single video source ?If Yes, please post link.

3. Is there anyone that has any idea/tutorial/howto (or however you' wanna call it) that may help me, and probabbly some other useres too ?

Thank You all in advance.

-------------------------------------
```
~$ uname -r
2.6.24-21-generic
```

---

