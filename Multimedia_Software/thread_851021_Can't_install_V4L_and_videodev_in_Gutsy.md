---
title: "Can't install V4L and videodev in Gutsy"
date: 2008-07-06
forum: Multimedia Software
---

### Post by disraeli on 2008-07-06
Hello everybody,
I have some troubles with installing a webcam at my girl's house but she lacks the v4l modules.

The system is Ubuntu Gutsy with the 2.6.22-15-generic kernel.

I already have two Ubuntu systems in my house, but they're equipped with Hardy and 2.6.24-19-generic kernel. In my case, I just plugged in the webcam and everything worked right away without the need to install anything.

The problem is, she has **no V4L module** - I thought it was automatically installed with Ubuntu as I have it in two different computers and I did not install it separately, nor do I find it into synaptic. It seems the only way is to download the sources and compile, even though this seems strange to me, no binary packages for ubuntu? Why didn't I have to compile v4l? Why do I have videodev and everything is working, and this is not the case with her?

Here is her lsusb output (the OmniVision entry is the webcam):

```
midori@midori:~$ lsusb
Bus 005 Device 006: ID 04f2:a221 Chicony Electronics Co., Ltd 
Bus 005 Device 004: ID 03f0:3b17 Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05a9:4519 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 06b9:4061 Alcatel Telecom SpeedTouch ISDN or ADSL Modem
Bus 002 Device 001: ID 0000:0000
``` 

Here is her v4l-info output:

```
midori@midori:~$ v4l-info
open /dev/video0: No such file or directory
```

And if I do a search for "v4l" inside her /lib/modules directory, I get these files only:

```
sane-v4l.man
snapscan.c
v4l.c
v4l.desc
v4l.h
v4l-frequencies.h
```

Would anyone please help me? The last thing I want her to do is downloading sources and compiling..

Thanks a lot!

---

### Post by weirdbeardmt on 2009-05-14
Did you get anywhere with this?

---

