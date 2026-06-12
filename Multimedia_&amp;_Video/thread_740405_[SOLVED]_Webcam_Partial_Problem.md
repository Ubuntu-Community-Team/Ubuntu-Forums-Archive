---
title: "[SOLVED] Webcam Partial Problem"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by 71fnRVVm on 2008-03-30
Hi everyone,

I managed to figure out most of the webcam stuff (using a Creative Live!Cam Notebook Pro... officially supported).  When I run "lsusb" I get:
```

Bus 005 Device 011: ID 0c0b:b311 Dura Micro, Inc. (Acomdata) 
Bus 005 Device 010: ID 0c0b:1140 Dura Micro, Inc. (Acomdata) 
Bus 005 Device 006: ID 05e3:0608 Genesys Logic, Inc. 
Bus 005 Device 002: ID 05e3:0608 Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 041e:4061 Creative Technology, Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 009: ID 10d5:55a2 Uni Class Technology Co., Ltd 
Bus 003 Device 008: ID 1b1a:0000  
Bus 003 Device 007: ID 1241:1603 Belkin 
Bus 003 Device 006: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

So, you see, it's on "Bus 004" and "Device 003", when everything I've seen has it as 1.

I can't get anything to connect to it.  Any ideas?

Thanks

---

### Post by linuxwizard on 2008-03-30
What have you tried using your webcam with ? Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing.

---

### Post by 71fnRVVm on 2008-03-30
Hi,

Yeah, I tried Ekiga, and tried changing the settings, but it doesn't recognize the device at all, let alone work.  Not under V4L and not V4L2.

I also installed and tried camorama, which just returns an error, and cameramonitor which doesn't show it as connected.

Thanks

---

### Post by linuxwizard on 2008-03-30
From here > [http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx) > you are going to need this driver > [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource)

---

### Post by 71fnRVVm on 2008-03-30
Ok, I had already installed the stuff from link 1 before posting this.

I "downloaded->make->make install->make clean"'d on the second link, but with no better results from any programs.

Thanks

---

### Post by linuxwizard on 2008-03-30
Did you reboot your computer after install of the driver ?

---

### Post by 71fnRVVm on 2008-03-30
Of course not... who does that?  It's Linux.

That being said, I'll have to finish up some things, reboot, and report back later.

Thanks

---

### Post by 71fnRVVm on 2008-03-31
Hm.  So the restart worked!  That's only the second time I've had "restart" be the answer to something not working (after installing updates/drivers/etc) on Linux...

Thanks though!

---

### Post by linuxwizard on 2008-03-31
You're Welcome Glad you got your webcam working. Yes reboots are rare in Linux but their are a few cases that you do need to reboot.

---

### Post by leandromartinez98 on 2008-06-29
I solved it as well. The exact way I did it is described here:

[http://ubuntuforums.org/showthread.php?t=660463](http://ubuntuforums.org/showthread.php?t=660463)

---

