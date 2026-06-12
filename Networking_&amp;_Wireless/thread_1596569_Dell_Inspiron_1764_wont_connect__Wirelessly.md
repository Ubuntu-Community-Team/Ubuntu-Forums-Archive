---
title: "Dell Inspiron 1764 wont connect  Wirelessly"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by michael.cordell on 2010-10-14
Brand new to ubuntu. i have a dell inspiron 1764 windows 7. it will connect wirelessly fine on windows 7 side but when i boot to ubuntu cant detect network or anything. what do i need to do.

---

### Post by stalker145 on 2010-10-16
Which version of Ubuntu are you using? 

I was using 10.04 until I decided to upgrade to 10.10 today. If you're using 10.04, go to the restricted drivers and enable STA. If you're using 10.10 like me, you may just be stuck. I've been reading around for the last couple of hours trying to find a fix.

I'll post here if I find something. Please do the same if you come up with an answer.

---

### Post by stalker145 on 2010-10-16
GOT IT!!

If you go [here]("http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html") and check for **bcmwl-kernel-source** on your system. If you have it, mark it for complete removal, then immediately reinstall, then restart, then enjoy the wireless happiness.

---

### Post by stalker145 on 2011-04-28
For anyone that's still running into problems with this after install 11.04, this method still works :D

---

