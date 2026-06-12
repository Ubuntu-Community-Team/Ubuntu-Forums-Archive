---
title: "KPPP and AT&amp;T and Network Manager"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by cigtoxdoc on 2008-12-23
What password do I enter when Network Manager asks me for the password for by sierra wireless air card?

I am using 8.10 and I cannot get my USBConnect881 device to work with Ubuntu.  I am using KPPP and trying to follow help guide from sierra wireless.

What am I doing wrong?

John

---

### Post by ieee488 on 2008-12-23
I use CINGULAR1

---

### Post by ieee488 on 2008-12-23
I use CINGULAR1
but supposedly you don't need to supply either username or password

---

### Post by cigtoxdoc on 2008-12-24
RE: AT&T USBConnect 881 (also from Sierra Wireless as air card 881U, also product is now "obsolete") running under 8.10.

Finally broke down and called AT&T.  After getting the run-around, and science fiction from several reps, finally got to speak with a rep who knew exactly what I was trying to do.  He had to refer to his notes, but we are now working.  Correct Sierra Wireless driver was already loaded on my PC (part of 8.10?), so the trick to make it work was how you filled in the blanks in KPPP and NetworkManager Applet.  KPPP as follows

Connect to: WWAN
Login ID: [email]ISP@CINGULAR.GPRS.COM[/email]
Password: CINGULAR1

on drilling down to modem tab:
uncheck wait for dial tone
on initialization string 1: OK,at+cgdcont=1,"IP","isp.cingular"
location /dev/ttyUSB2
number to dial *99***1# or *99#
authentication is PAP/CHAP

One NetworkManager applet only fill our number to dial, your AT&T username and AT&T password.

When you plug your modem in, it should take off.

John

---

