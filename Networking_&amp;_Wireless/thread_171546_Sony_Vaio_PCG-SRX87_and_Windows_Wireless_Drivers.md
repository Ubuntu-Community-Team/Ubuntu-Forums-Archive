---
title: "Sony Vaio PCG-SRX87 and Windows Wireless Drivers"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by andymatic on 2006-05-06
I've made some progress but am still stuck.

Hardware is a Sony Vaio PCG-SRX87 ([specs/info]("http://esupport.sony.com/US/perl/model-home.pl?mdl=PCGSRX87&LOC=3")) running Ubuntu 5.10 (dual-boot with a WinXP install).

I installed the Windows Wireless Drivers program after reading about others' success.

I found the wireless driver for my machine while booted in Windows by using Device Manager. I moved a copy of that driver over to the Ubuntu partition and then added it to the 'Currently Installed Windows Drivers' in Windows Wireless Drivers which returns a 'Hardware present: No' error.

I even tried the route of downloading [the EXE drivers from the Sony Support site]("http://esupport.sony.com/US/perl/swu-download.pl?mdl=PCGSRX87&upd_id=419&os_id=7") and using Unshield and Cabextract to extract the driver file ('wlluc48.sys') but that didn't work either.

In 'Network Settings' the Wireless conection (called 'eth1') says it is active. But when I try to browse without the actual ehternet cable (connection 'eth0') plugged in, I can't access the pages.

Any ideas what to try next?

---

### Post by andymatic on 2006-05-07
Wow. It's always the tiny thing you don't double-test. After much gnashing of teeth and trying to get Orinoco drivers to work I think I figure it out: I had the connections WEP key set to Plain Text when I have my router configured as Hexadecimal.

---

