---
title: "How install a Chicony webcam? HELP"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by viper78 on 2007-03-11
Hi!
I have ubuntu-dapper 6.06 LTS with all updates. All devices works good, except my webcam Chicony DC5132 (iCam5320) Panda 8b,black/grey,300k,microhpone,snap shot, usb1.1, see picture below.

1. EasyCam, see [**[COLOR="Purple"]Thread1[/COLOR]**]("https://help.ubuntu.com/community/Webcam") returns:  ***NO CAMERA, OR NO COMPATIBLE CAMERA FOUND***
Camorama start, but in picture I see my TvTunner device.
2. Epcam, see [**[COLOR="Purple"]Thread2[/COLOR]**]("http://ubuntuforums.org/showthread.php?p=2043563"), returns no errors, but nothing changed, kopete see my tvcard, not webcam device.
3. Ov51x, see [**[COLOR="Purple"]Thread3[/COLOR]**]("https://help.ubuntu.com/community/Ov51x"), no errors instalation but the webcam don't work.

Please, someone help me! I am so tired! I have only ubuntu instaled and my webcam is unusuable.
The led's webcam is lighting.

---

### Post by teaker1s on 2007-03-12
Okay lets try this from a different angle, as I understand it you have tried various web cam tutorials and are fustrated because it still won't work and are unsure of the chipset of camera.

If we find what chipset the camera has we can then look for a driver/support for it.
Terminal
```
lsusb
```
if you need help identifying your camera in the terminal output, then please post it here

:guitar: :guitar: :guitar:

---

### Post by buchannon on 2008-04-15
I'm having issues getting my integrated toshiba webcam working as well if you don't mind still helping teaker... 

Here is the output from my lsusb:
> 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

---

### Post by teaker1s on 2008-04-15
[http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/")
googling appears v4linux2 supports this camera

---

