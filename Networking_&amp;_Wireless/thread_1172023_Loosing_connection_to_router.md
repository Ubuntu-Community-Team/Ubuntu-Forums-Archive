---
title: "Loosing connection to router"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by mikblehm on 2009-05-28
I am running Ubuntu 9.04 with a linksys wusb100 adapter.  I also have a linksys wrt54g router.  When I start ubuntu my connection is fine but it will drop at random intervals and requiers a restart of the computer to reconnect.  I'm using ndiswrapper and windows xp driver.  any ideas as to the problem?  any help would be nice as I'm kind of new to linux.

---

### Post by ralley4 on 2009-06-07
> **mikblehm said:**
> I am running Ubuntu 9.04 with a linksys wusb100 adapter.  I also have a linksys wrt54g router.  When I start ubuntu my connection is fine but it will drop at random intervals and requiers a restart of the computer to reconnect.  I'm using ndiswrapper and windows xp driver.  any ideas as to the problem?  any help would be nice as I'm kind of new to linux.



Incase you are still having problems with your adapter, I have found a solution that has worked for me.

It consists of using a native driver that Ralink has released and apparently, keeps up to date. I tried the NDISwrapper method, and it showed the driver was loaded. However, I never could get connected, so I looked elsewhere. I read a thread (link #1 below) that had a link to the Ralink website (link #2 below), and I went that route instead.

1) [http://www.linuxforums.org/forum/wireless-internet/118831-wusb100-help-please.html](http://www.linuxforums.org/forum/wireless-internet/118831-wusb100-help-please.html)
2) [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

On the Ralink driver page, I downloaded the RT2870USB(RT2870/RT2770). I followed the steps from the file: README_STA, included in that zip file.

Everything is working great for me at this point. I noticed this morning that I have to repeat step 6 every time I reboot though. I would like to find a solution for that. I'm sure it is pretty simple, but since I'm a semi-noob, I'm not sure what to do. I just started using linux again after several years, btw.

I hope this helps you.

Cheers!

---

### Post by jessica alice on 2012-06-19
i use ubuntu 11.04 in  my computer...i use smartbro and the connection interrupts me whenever i am in use..what will i do to make the connection fast?any suggestion? i'm very new to ubuntu, please help me...

---

### Post by Perfect Storm on 2012-06-19
Necromancing (old thread brought back to life). Please start a new thread instead.


Thread closed.

---

