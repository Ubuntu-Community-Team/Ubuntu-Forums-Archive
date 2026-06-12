---
title: "V2000 Presario wifi - need firmware help"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by larryj54 on 2011-08-19
Chili555 I need a file you linked in a 2010 solution.

Brand new user with a partitioned Compaq Presario V2000.  WiFi not working and I found the identical problem and solution, but the firmware download specified no longer works..

NOT FOUND - The requested URL /pool/jaunty-cafuego/broadcom/b43-firmware_1.1-0cafuego1.tar.gz was not found on this server.

so please help me find this firmware file so I can get this WiFi working.

here is the thread from 2010 where Chili555 describes the exact problem and solution; and refers to the Page to D/L the firmware.

[http://ubuntuforums.org/showthread.php?t=1441691](http://ubuntuforums.org/showthread.php?t=1441691)

Again, all I need is a good link to this firmware, then I can follow the excellent instructions by Chili555.

Thanks, LarryJ

---

### Post by larryj54 on 2011-08-20
I wonder if my reply will be ignored as well as my problem.  I have TRIED to NOT bother anyone with a common problem.  But for all the solutions I have tried to follow from other seemingly exact same issues as mine, the solution does not work.

I cannot find ANY drivers in the Systems/admin/hardware drivers area; it says there are no proprietary drivers in use on this system.

IN almost every thread the person is told to do some superuser command (that I cannot recall to post) that has fwcutter, b43-firmware, etc in it.  THIS never works.. I have a wired connection just like the solutions say to do.  This file or whatever cannot be found.

The problem is frustrating enough, but being ignored for some offense I evidentally have committed but cannot understand is REALLY frustrating!

What exactly have I done to offend?

---

### Post by chili555 on 2011-08-20
I doubt that anyone thinks you committed even the slightest offense. Rather, I imagine that when people read my name, they laughed and said, hey chili555 created that problem; let him clean it up! Sadly, I didn't see your post until just now. I'd like to read each and every thread, but I just can't.

Here is a file with the firmware in it. Download it to your desktop and right-click it and select Extract Here. Then open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo chown root:root /lib/firmware/b43/*
```Reboot and see if your wireless is working. If not, maybe b43 firmware is not correct for your device. In that case, post:```
lspci -nn | grep 0280
```In the future, please feel free to send me a private message and give me a link to a thread you've posted. I'll be glad to help.

---

### Post by larryj54 on 2011-08-20
Chili555!!!!  You are there!!  Thanks, but perhaps you will be happy to know that I solved my own problem.  I went searching and found a site that referred me back to Ubuntu Forums, where I finally found the answer to my whole problem: Where in heck are these files I need?  Turns out they are on my Ubuntu CD, in the pool/main/b/b43-fwcutter....

I just had no idea where to find the files your otherwise excellent directions alluded to.  Once I found this file on the CD, it was Bada-Bing-bam-boom, done!  Works.

Thanks for responding though.  I thought I did a bad. ;)

LarryJ

---

### Post by chili555 on 2011-08-20
Awesome, sir! Glad it's working.

---

### Post by morgad on 2011-08-28
Had the same problem myself today on my V2000, thanks to your hint I went into synaptic and installed the 'firmware-b2-installer' package.
10 seconds later working wireless :)

Thanks
Dave

---

