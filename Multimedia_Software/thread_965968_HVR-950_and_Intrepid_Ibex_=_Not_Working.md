---
title: "HVR-950 and Intrepid Ibex = Not Working?"
date: 2008-11-01
forum: Multimedia Software
---

### Post by tmeitner on 2008-11-01
Hello, I'm really hoping someone can help me out here. I was running MythTV with a WinTV HVR-950q USB video capture card (for the HD) in Ubuntu Hardy and had everything set up and working fine (eventually). Hardy's kernel updates wound up causing my card not to work. So I had to boot into an older kernel for it to work. I heard that Intrepid Ibex would natively support the 950, so I upgraded. Now, it won't work! Every time I try to watch live TV, I get a black screen, and nothing is recording when it should.

I've spent a lot of hours trying to fix this and I would be forever indebted to anyone who could help me fix this problem - I miss my HD PVR! I'm willing to post any information about my system that you need.

---

### Post by dliloch1 on 2008-11-01
hello,
I don´t have an answer but I can confirm that I am having the same problem with my wintV-HVR950 usb TV receiver under 8.10 ibex and using XAWTV. It recognizes the device can configure the channels but black screen and no audio. This occurs under native linux and under vmware using windows xp and running wintv software.

Now under 8.04-lts hardy it works fine under vmware....

---

### Post by jtonk on 2008-11-02
hello,

I might be having the same problem after upgrade to 8.10, but i'm then using the pvr 150 and pvr 500. When the drivers are initially loaded on boot they work fine using mplayer

mplayer /dev/video0

but when I use them in mythtv they won't work. /var/log/mythtv/mythbackend.log gives me 

2008-11-02 11:42:30.334 MPEGRec(/dev/video2) Error: select timeout - ivtv driver has stopped responding

It looks like mythtv and ivtv are not working properly.

regards

Jasper

---

### Post by KvZ on 2008-11-02
Hi,

Can also confirm the same issue, device is recognized, but no video or audio and MythBackend log reports the "select timeout - ivtv driver has stopped responding" error.

It looks like a issue with the ivtv driver in kernel 2.6.27-7, according to dmesg this is version 1.4.0. When I boot with kernel 2.6.24-21 my pvr 150 works fine this has ivtv version 1.1.0.

Any ideas??  

Thanks
Karsten

---

### Post by KvZ on 2008-11-02
Hi all,

In my case I resolved the issue by installing the Bleeding Edge version of the ivtv drivers see: 

[http://www.ivtvdriver.org/index.php/Download](http://www.ivtvdriver.org/index.php/Download)

Thanks
Karsten

---

### Post by jtonk on 2008-11-02
Tnx Karsten,

I can confirm that in my case the bleeding edge driver also seems to work for the PVR 150 and PVR 500. Hope this gets into the next kernel version. Do we need to file a bug? how do you do that?

regards

Jasper

---

### Post by whitty on 2008-11-02
Hey all, the last thing I want to do is threadjack, but I've been trying to set up my HVR-950Q under 8.04 for MONTHS with no success. I can install the drivers to get the card recognized no problem, mythtv install was as easy as apt-get install ever is, but for the life of me I can not scan channels. I had given up to wait for 8.10 to see if things magically worked now, but it seems it will still be a bit of work. I'm going to try setting up 8.10 with the bleeding edge drivers, but for those of you who have everything working, I simply ask HOW?! Any chance you could provide me with a rough guide to getting things set up after the tuner and mythtv are both installed? I'd take a PM just to keep the thread on topic, although since it'd be useful information, i'd also take just posting it as a reply or starting a new how-to thread and linking. However though, I'm desperate. 

Thanks a ton if you can help,
Alex

---

### Post by period3 on 2008-11-08
I have the same problem.  I haven't been able to use my PVR 950 since I bought it several months ago.  I just upgraded to Intrepid, and it doesn't work there either.

It appears to be recognized:
[    1.277315] pci 0000:01:00.0: Boot video device
[   12.320407] Linux video capture interface: v2.00
[   12.916813] em28xx new video device (2040:6513): interface 0, class 255
[   13.501276] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0


But I can't get it to work with mythtv, (nothing happens when I click watch tv, despite setting it up in mythtv-setup), xine (No DVB input device found), or mplayer (Playing /dev/video0. Cannot seek backward in linear streams! Seek failed).

Is there a proper howto for the 950 anywhere?  I originally bought it because it was *supposed* to be supported in linux (eg. [http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html](http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html))  

I certainly haven't had any luck though.




> **whitty said:**
> Hey all, the last thing I want to do is threadjack, but I've been trying to set up my HVR-950Q under 8.04 for MONTHS with no success. I can install the drivers to get the card recognized no problem, mythtv install was as easy as apt-get install ever is, but for the life of me I can not scan channels. I had given up to wait for 8.10 to see if things magically worked now, but it seems it will still be a bit of work. I'm going to try setting up 8.10 with the bleeding edge drivers, but for those of you who have everything working, I simply ask HOW?! Any chance you could provide me with a rough guide to getting things set up after the tuner and mythtv are both installed? I'd take a PM just to keep the thread on topic, although since it'd be useful information, i'd also take just posting it as a reply or starting a new how-to thread and linking. However though, I'm desperate. 

Thanks a ton if you can help,
Alex

---

### Post by dliloch on 2008-11-16
finally got it to work with my vmware xp virtual machine. What made it work for me was upgrading the xp drivers with version 4.6a from the Hauppauge site. The cd that came with my device was apparently out of date. Acutually this is better than 8.04 because the audio is finally in sync. :)

---

### Post by dliloch on 2008-11-16
well .. sort of working .. ran for a few hours then I had to close down the virtual machine .. hung up .. when I restarted I would not get picture or sound. Reinstalled drivers then it worked again.

---

### Post by Skivache on 2008-11-19
I'm glad to see some others having similar issues (well, kinda).  I'm am trying to use my HVR-950's composite input with analog camera in zoneminder. Without any tweaking, if I plug the tuner in and run xawtv, I can view the feed from the camera.  Unfortunately, I've had no luck viewing the feed in anything else including mplayer.  I don't know if I should try upgrading the the bleeding edge drivers because it already works for what I need it to do. Did anyone try their working and not working tuners with the composite input?

---

### Post by emptiness on 2008-11-29
I'm having similar problems with my eyetv hybrid (essentially a HVR-950Q) tvtime wants to use my macbooks built in camera instead of the tuner and I can't change the device from the menu.
I dunno what I'm doing wrong?!

---

### Post by siepo on 2008-12-02
You could try to edit ~/.tvtime/tvtime.xml which has a line

<option name="V4LDevice" value="/dev/video0"/>

Try replacing video0 with video1

---

