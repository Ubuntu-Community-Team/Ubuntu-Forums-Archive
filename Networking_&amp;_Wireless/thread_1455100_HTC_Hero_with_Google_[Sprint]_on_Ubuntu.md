---
title: "HTC Hero with Google [Sprint] on Ubuntu"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by mwielgosz on 2010-04-15
Hello,
First of all I'm new to this forum...I've been reading it for a while, but now have a reason to post on here. :)  Hello community!

So onto my question.
I'm looking into a new cell phone.  I use Xubuntu 9.10 exclusively and refuse to install any Microsoft software onto my computer at all.  I've been using different variations of Linux for around 7 years now, so I'm no newbie.

Since phones with the Android OS have come out, I've been very interested.  Particularly, the HTC Hero with Google has caught my attention.  For my email, contacts, and calendars, I use Google, so this phone seems to fit the bill.  The only thing I cannot seem to find information on is using the phone as a modem with Linux.  There's scattered information on the subject, and there seems to be no definitive answer.

So, has anyone used the Sprint HTC Hero with Google and successfully used it as a wireless modem with Ubuntu 9.10 (or any version of Linux for that matter)?  If so, how well does it work, and how difficult is it to set up.

I currently have a Blackberry, and I'm not satisfied at ALL with the Linux support for it.  The Barry project is decent, but does not provide what I need.  Specifically, using the Blackberry as a modem in Linux is basically a hack.  I'm really hoping that the HTC Hero with Google will have better support since it's basically built on a Linux OS.

If no one has actually used the HTC Hero with Google with Linux, is there any other PDA/SMART phone which Sprint currently offers that allows easy modem access?


This is a link to the phone I'm currently looking at:
[http://www.mobiledia.com/phones/htc/hero.html](http://www.mobiledia.com/phones/htc/hero.html)

Thank you community.

---

### Post by jmkemp on 2010-05-29
Just spotted your post when trying to find decent info to set up my wife's new Blackberry Curve 8250. I've had an HTC Hero (called a G2 by T-Mobile in the UK) since September 2009. 

You'll not find much about using it as a modem because it is trivial to do this and it comes with a menu setting. So no messing around is required. Steps are:
1) plug the HTC Hero in using the USB cable that comes with it;
2) on the phone press the 'MENU' button, choose Settings|Wireless Controls|Mobile Network Sharing;

Ubuntu then finds the network and uses it as USB0 (on my box). There were some issues with network manager on 9.10 meaning you had to plug it all in and reboot, but this is fixed in 10.04. 

Hope this helps.

---

