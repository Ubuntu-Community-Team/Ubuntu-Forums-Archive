---
title: "WUSB100 v2 Adapter Help. Almost working..."
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by c_was on 2010-11-01
Running Ubuntu 10.10, and I can't get my WUSB100 v2 Linksys adapter to work. I've tried what's in this thread:

[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

Entered lsmod |grep rt into Terminal and found out it runs on the rt2800 chipset, so I blacklisted everything necessary. It finds and connects to my network but after about 10 minutes it disconnects and won't reconnect.

Help..?

---

### Post by MooPi on 2010-11-01
Can you list what you've blacklisted ?

---

### Post by c_was on 2010-11-01
I've removed all of the blacklists for now. But when I blacklisted rt2870sta, that's when it would connect for a few minutes. I've tried adding the device ID and compiling the rt2870sta driver that came with the system, and then blacklisting the rt2800, but that doesn't work.

---

### Post by c_was on 2010-11-01
I'm basically brand new to Ubuntu so maybe you could tell me some code that would give you all the info you need?

---

### Post by c_was on 2010-11-01
Anybody?

---

### Post by c_was on 2010-11-01
Bump..

---

### Post by bernardfrancois on 2010-11-14
The instructions in this thread did the trick for me:
[http://ubuntuforums.org/showthread.php?t=1602271&highlight=linksys+WUSB100](http://ubuntuforums.org/showthread.php?t=1602271&highlight=linksys+WUSB100)

 I also have a Linksys WUSB100 Ver.2 (as written on the stick itself).

Good luck with it!

---

