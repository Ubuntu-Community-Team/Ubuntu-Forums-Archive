---
title: "Internet without bootable CD"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by vasimakhtar on 2006-06-05
Hi,
I have installed Ubuntu with dual booting on winxp. When I boot Ubuntu with bootable CD, I am able to access internet. Whereas when I boot without CD, I won't.
Will appreciate replies on the same. I am using MOTOROLA SB5100 modem for cable internet connection.
The same connection is working perfectly in WinXp and with bootable CD in ubuntu.
Thanks

---

### Post by rado_london on 2006-06-05
Did you try to configure the network in System-Administration-Networking?

---

### Post by vasimakhtar on 2006-06-05
Yes I did. I tried to activate-deactivate option, but it didn't work. I called to my ISP also, but they said, they don't provide support for Linux. I wondered.

---

### Post by hektisk on 2006-06-05
Do you have a Davidcom Semiconducter ethernet card?  Check this out: [http://ubuntuforums.org/showthread.php?t=186430](http://ubuntuforums.org/showthread.php?t=186430)

I have a Davidcom and had the same exact problem as you - worked fine with CD, didn't work at all without.  I ended up changing cards (I didn't find that other thread until just now) but that should work if you do.

---

### Post by vasimakhtar on 2006-06-06
Hi,
How can I know which ethernet card I am using?. I am not sure that I have Davidcom or else. Is there any command to know that?
thanks

---

### Post by vasimakhtar on 2006-06-06
Is anyone having solution for the said problem? My work is heldup because of internet access. Will appreciate reply.
thanks

---

### Post by vasimakhtar on 2006-06-06
Hi,
I have installed Ubuntu with dual booting on winxp. When I boot Ubuntu with bootable CD, I am able to access internet. Whereas when I boot without CD, I won't.
Will appreciate replies on the same. I am using MOTOROLA SB5100 modem for cable internet connection.
The same connection is working perfectly in WinXp and with bootable CD in ubuntu.
Thanks

---

### Post by hektisk on 2006-06-06
[QUOTE=vasimakhtar]Hi,
How can I know which ethernet card I am using?. I am not sure that I have Davidcom or else. Is there any command to know that?
thanks[/QUOTE]

Type "lspci" in terminal.  It'll list your hardware.

---

