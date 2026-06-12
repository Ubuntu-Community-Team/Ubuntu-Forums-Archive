---
title: "Random wireless disconnects - 9.1/Toshiba/Intel 3945abg"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by brons2 on 2010-02-22
Hello,

I have my laptop dual booted between Ubuntu 9.10 and Windows 7.  

In Ubuntu I randomly lose connection to the wireless network.  It always works fine when I first boot into Ubuntu but after a while my wireless connection will go down.  The signal strength meter will go to zero bars and the black popup message will appear that my wireless connection has disconnected.  At first, if I just wait a bit, the connection will come back.  However, after about 4 or 5 times of doing this it will then ask me for my password, and inputting the password does not reconnect me to the AP.  I am finally forced to reboot.  Then it works OK for a while again and the cycle repeats.

It works fine in Windows7 all day, every day.  I have the Release Candidate of Windows7 so it's going to expire soon.  I would really prefer to make Ubuntu my everyday OS on this laptop rather than pay for a Windows7 license but I cannot tolerate a flaky wireless connection.  

I had 8.1 on this laptop at one point and I never had any problems with the wireless then, that I can remember.  I had no Ubuntu for a while but then I came back with the 9.1 and was loving it until the wireless problem reared it's ugly head.

Wireless found by lspci:
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Any help appreciated...

---

### Post by brons2 on 2010-02-22
Seems to be a known issue.  Pathetic.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204)

Also confirmed from other people that it worked fine on Intrepid.  Where's the testing?!?!?

---

