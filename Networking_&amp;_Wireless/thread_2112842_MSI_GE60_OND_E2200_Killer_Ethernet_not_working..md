---
title: "MSI GE60 OND E2200 Killer Ethernet not working."
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by Muppet1996 on 2013-02-05
So i've been trying to get ubuntu to work properly on my Msi ge60 ond laptop and one of the things that is not working is the ethernet, the operating system recognises the card. It's just that theres no driver for it, and from searching around on google i found that there isn't a driver for it out yet. The only thing i found was the solution at [http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332) and unfortunately enough that didn't work, even though i followed the exact steps. This includes other posts from others. (it was recognized in the kernel module list (lsmod), and everything went flawlessly, no error messages).
Hopefully somebody could help me out on this, i'm still fairly new to linux in general.

This is some information about the laptop:
Brand and type: MSI GE60 OND 
Card: Atheros killer E2200 ethernet
lspci -nn | grep 0200: Atheros Communications Inc. Device [1969:e091] (rev 13)
ifconfig: Only wlan0 is recognized, the eth0 is nowhere to be found.

As said before what i've tried is the steps on this post: 
[http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332)

Thanks in advance! ):P

---

### Post by Muppet1996 on 2013-02-05
Got it to work :guitar:. What i was doing wrong was the patching, i only ran with --dry-run. Ran it with --dry-run first, and then without after for both patches and it worked. 
Used the compat-wireless-3.5.4-1-snpc package, alongside the 3.5.0-23-generic kernel. 

Thankyou [Mahler122]("http://ubuntuforums.org/member.php?u=649404") and [belnac]("http://ubuntuforums.org/member.php?u=1023215"), you just made someones day 20x better.

This can be locked.

---

