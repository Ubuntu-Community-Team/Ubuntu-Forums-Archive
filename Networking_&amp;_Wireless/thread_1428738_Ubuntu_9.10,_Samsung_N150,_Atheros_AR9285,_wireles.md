---
title: "Ubuntu 9.10, Samsung N150, Atheros AR9285, wireless detected but cannot connect"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by Martin.Wit on 2010-03-13
Hello Everyone,
This is my first post, although I've been lurking for some time.

I have a Samsung N150 netbook with Atheros AR 9285 WiFi card. 
I installed Ubuntu 9.10 on it, although this problem happens on other distros too (Network Remix 9.10, OpenSuse 11.2)

My wifi card and networks get detected. The problem is when I try to connect to my network, which is protected by WPA key (I don't know if it matters whether it's WPA or not). 
After I input my network key, the network manager is trying to connect, but obviously cannot, because just prompts me for password again. 

I can connect without problems to this network from my other computer running WinXP, so wrong password and such is out of the question.

Anybody has any idea what might be the reason? 

I am a beginner Linux user and I hate Win7 but then, I will have to switch back if I cannot connect my WiFi. 

Any help or idea will be warmly welcome!

Martin

---

### Post by vargad on 2010-03-14
Hello, I have exactly the same netbook with exactly the same Atheros card. It works perfectly for me, I usually connect to a WPA2 access point.
I use gentoo linux, with Linux kernel 2.6.30 (it's a waste of time trying gentoo because of this wireless issue).
Atheros driver built in the kernel so it should work with Ubuntu 9.10 (it has linux kernel 2.6.31).
However I found a thread about this: [http://ubuntuforums.org/showthread.php?t=1244686](http://ubuntuforums.org/showthread.php?t=1244686)
They have the same problem with this Atheros card, however they use older Ubuntu with older kernel. I think it should work well with Karmic. They installed the backports (on Ubuntu 9.04) in order to get the driver you currently use, but you can also try to install the backports modules, maybe there is a newer backported Atheros module wihich works.
You should attach more information about your problem:
- dmesg
- lsmod
- Network Manager log (I don't know here you can find it)
I use wicd not Network Manager to connect, you can try it if you want, but it probably won't fix the problem, maybe help to debug it. Wicd has quite detailed log: /var/log/wicd.log
Wicd guide for Karmic: [http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu](http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu)
Maybe someone who know Network Manager better can help you.
All in all if it is a driver problem installing a newer kernel probably solve your problem. It can also be a bug in Network Manager, maybe it works with wicd. It should work, happy bug hunting.

---

### Post by Ernie S. on 2010-04-05
[http://ubuntuforums.org/showthread.php?t=1447643&highlight=atheros+9285](http://ubuntuforums.org/showthread.php?t=1447643&highlight=atheros+9285)

---

### Post by buntu_hugenewbie11 on 2010-04-16
Upon reinstall of ubuntu remix my touchpad stopped working.
Anybody have any idea as to how to get the touchpad working on Remix 9.10 for Samsung N150?

---

