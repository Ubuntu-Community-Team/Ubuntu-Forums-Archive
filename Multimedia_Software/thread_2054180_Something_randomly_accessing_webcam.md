---
title: "Something randomly accessing webcam?"
date: 2012-09-06
forum: Multimedia Software
---

### Post by LastHylian on 2012-09-06
I have a Microsoft HD LifeCam that I'm using in conjunction with motion and a bash script I wrote to act as a proximity sensing security camera. I can tell the camera is starting up or active by the blue LED on the front.

At seemingly random times, the camera LED will blink as if it is starting up or even stay constant for a few moments before going back off. I have checked numerous times and verified neither motion or my script is running. My overall question is "Is there a quick way to see which programs are tapping into my /dev/video0 device?"


lsusb ouput :
```
Bus 001 Device 003: ID 045e:076d Microsoft Corp. LifeCam HD-5000

```

Perhaps it is not relevant, but I noticed these in dmesg. Motion is not running.
dmesg output
```
[939500.075450] motion[3762] trap stack segment ip:4218b5 sp:7fe4ec03d970 error:0
[939500.277423] motion[3751] trap stack segment ip:4218b5 sp:7f9f03fbe970 error:0
[939500.315959] motion[3816] trap stack segment ip:4218b5 sp:7f1b2a53d970 error:0
[939500.407781] motion[3700] trap stack segment ip:4218b5 sp:7ff1c46fe970 error:0
[939504.870719] motion[4277] trap stack segment ip:4218b5 sp:7f84b82e3970 error:0

```

Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

Any other data needed? Thanks in advance

---

