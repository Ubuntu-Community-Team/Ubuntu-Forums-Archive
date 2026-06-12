---
title: "Realtek 8188SU USB Wireless -- how do I install the drivers?"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by marcoharder on 2010-09-13
Hi everyone!
 
I've been using Ubuntu for almost a year now, but I have to admit, I'm still a noob compared to most of the guys here who readily and happily help people out like me.
 
Anyhow, my problem is this. I just bought a Realtek USB Wireless Adaptor and downloaded the drivers. However, the instructions on the driver zip went like this, and frankly, have not worked for me:
 
step1: uncompress the “rtl8712_8188_8191_8192SU_usb_linux_v2.6.x.x.2010xxxx.tar.gz” file. (in “driver” directory)
> tar zxvf rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20100625.tar.gz
 
(2) step2: make 8712 USB driver module
> make
 
(3) step3: clean the operation environment
> ./clean
 
(4) step4: insert 8712 USB modules 
> insmod 8712u.ko
 
(5) step5: enable wlan0 interface
> ifconfig wlan0 up
 
(6) step6: setup IP address
> ifconfig wlan0 192.168.1.100
 
My question is, will these instructions work with Ubuntu? The instructions file says that it's for a Fedora Distro. 
 
Cheers!
 
MH

---

### Post by MaindotC on 2010-09-13
The drivers should already be installed in Ubuntu.  Post the output of:```
lshw -C network
```

---

### Post by marcoharder on 2010-09-13
Ok, I will do that later. Thanks!

---

### Post by marcoharder on 2010-09-14
After much googling, I finally found an old post containing chili555's instructions and by god, they worked! 

I just have a general question though: how do I KEEP the driver installed permanently? I rebooted earlier only to discover that I had to go through the instructions again just to go online.

---

### Post by barnaclekarl on 2010-09-14
I made a post about a Realtek 8190 card a week or two ago. I had great success sending Realtek support an email with my version info. After only a couple of (business day) hours, I received the correct driver in an email. su, make, make install, reboot, and viola!

I recommend this over some of the alternative work-arounds. It is working like it should.

---

### Post by MaindotC on 2010-09-14
> **marcoharder said:**
> After much googling, I finally found an old post containing chili555's instructions and by god, they worked! 

I just have a general question though: how do I KEEP the driver installed permanently? I rebooted earlier only to discover that I had to go through the instructions again just to go online.

I need to see a link to that post please.  If you are using modprobe then once you modprobe the driver it should stay in there unless it is blacklisted in the /etc/modprobe.d/ directory.

---

### Post by marcoharder on 2010-09-15
I just realised I forgot the modprobe bit the first time around. Anyway, problem solved and Ubuntu community help wins again!

---

### Post by MaindotC on 2010-09-15
Wonderful!  Please mark the thread as solved and edit your first post to state "Update:" and the solution so other users do not have to read the entire thread.

---

### Post by Andreg69 on 2010-11-14
I am a newbie to Ubuntu - just installed maverick this week as a clean install - no windows at all on this hard drive.  Advised by friends that it is excellent but I have to say I am not sure yet.  It is proving a little difficult to get it working properly even for basic web browsing.  I'm happy to invest some time learning though.

Having followed the above thread I have also succesfully installed the driver that I downloaded.  The problem is I don't know how to do the modprobe bit.  So every time I reboot it wont connect to the network.  Please help...

---

