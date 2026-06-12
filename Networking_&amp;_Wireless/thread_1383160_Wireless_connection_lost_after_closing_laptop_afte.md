---
title: "Wireless connection lost after closing laptop after 9.10 Upgrade"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by homeuser1 on 2010-01-16
I have an odd problem in that my wireless connection is okay until I close the laptop.  When I open it back up, I'm unable to reconnect.  This problem first occurred after upgrading to 9.10.  I can reconnect after restarting. I tried several things before breaking down and reinstalling 9.04. After installing 9.04, everything works great.  Any suggestions on what is going on before I try upgrading to 9.10 again?  I have a Dell D600.

---

### Post by homeuser1 on 2010-01-18
I reinstalled 9.10 and the same result.  Every time I close the laptop it kills the wireless network. Hopefully, the next upgrade solves the problem.

---

### Post by homeuser1 on 2010-01-24
Here's a little more info.  So,the last time I installed 9.10 I partition the hard drive to allow me to have 9.04 and 9.10. I recently booted up using the 9.10; 2.6.31-14 kernel. Using this kernel, there were no problems with the wireless connection being permanently killed.  When I open the laptop, the network manager reconnects and we're off and running.  I retried the 2.6.31-17 kernel and the same old bug is present.  The network manager doesn't even attempt to reconnect automatically and I can't manually make it reconnect unless I restart.  Hope this helps someone fix 10.04.

---

### Post by homeuser1 on 2010-02-06
New update:  The recent kernel update 2.6.31-19 did not fix the network connection problem first encountered with the 2.6.31-17 kernel. As soon as I close the laptop the network connection is killed and only a restart will allow the network to reconnect.  So for now, I'll use the 2.6.31-14 kernel.  It works perfect.

---

### Post by claracc on 2010-02-07
I use wicd instead of network manager gnome to control wifi.

Network manager gnome never worked for me with 9.10 karmic Koala, wifi connected and disconnected all the time, doing internet unusable.

---

### Post by ccphilly1984 on 2010-02-07
> **claracc said:**
> I use wicd instead of network manager gnome to control wifi.

Network manager gnome never worked for me with 9.10 karmic Koala, wifi connected and disconnected all the time, doing internet unusable.

dude, i had the same problem... now with wicd, my wifi is no longer intermittent... i can stream media to my xbox 360 and download torrents seamlessly... 

that being said, using wicd, after i close my netbook and reopen it, i get no network and if i open up wicd, it crashes the operating system... i changed to ubuntu netbook remix because i was sick of this windows type crap :mad:

---

### Post by Tlynyrd on 2010-02-07
Hi,
So I guess using wicd is not the best solution?? I'm having same problem, when I shut the lid and re-open it I loose wifi, occasionally I can re-connect manually, but most of the time I have to re-boot...   :o(  It took long enough to find a driver for the wifi to get it to work, but now this is happening...  I'm very new to Ubuntu,  and have hardly any knowledge of Linux, so please be kind with your answers...  
HP DV6700, AMD Turion 64, 3gig memory, 160gig HD, 
Running Ubuntu 9.10 Koala
Thanks in advance,
Tlynyrd

---

### Post by homeuser1 on 2010-02-08
Hey, I'm sort of glad to know there are others.  I was starting to think I was the only one with this problem.  

For me, I reinstalled 9.04 on it's only partition.  Now when I reboot, I have the option to select which kernel I want to boot to.  I now select 2.6.31-14 of the 9.10 release.  Hope that helps.

Maybe someone will figure this out on a new release. :)

---

### Post by homeuser1 on 2010-05-23
The 10.4 upgrade fixed the problem.  So far 10.4 is working great.  NO complaints.

---

