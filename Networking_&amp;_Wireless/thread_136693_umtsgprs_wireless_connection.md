---
title: "umts/gprs wireless connection"
date: 2006-02-26
forum: Networking &amp; Wireless
---

### Post by moises73 on 2006-02-26
Hi all, 
i live in germany and at my house i can get isdn internet, but the company told me the hub is so far that the connection is as fast or slower than what dial-up would be. so we found an alternative. with vodafone, i got this pcmcia card that works the same as the receiver of a mobile phone. the thing is that the drivers they gave me are for windows and mac. so my question is, has anyone attempted to connect to the net with this type of device or does anyone know if there is linux driver for it. here the info that is on the card:

Option Wireless Technology
Qualcomm 3G CDMA
Model: GT 3G Quad
Designed in E.U. by Option
Datacard: UMTS/GPRS

i really hope someone can help, i will be googling myself.

thanks

---

### Post by joft on 2006-02-27
Hi,

some time ago I also tried to use such a card with linux. I found several HOWTOs:

[http://www.pharscape.org/index.php?option=content&task=view&id=28](http://www.pharscape.org/index.php?option=content&task=view&id=28)

[http://www.pharscape.org/index.php?option=content&task=view&id=30](http://www.pharscape.org/index.php?option=content&task=view&id=30)

[http://www.pharscape.org/index.php?option=content&task=view&id=29](http://www.pharscape.org/index.php?option=content&task=view&id=29)

But I never got my card working. I was able to get past the PIN check, but I never got any connection. And since then (half a year ago), I didn't try it again.

If you get it working, I'd be interested in how you did it :)

---

### Post by moises73 on 2006-02-27
thanks joft,

i worked with the link for the 3G, is the one that seemed more accurate.  but there is no modprobe.conf in /etc/  should i add one and insert the lines that the guide provide.

at first ubuntu would not recognize the card, it would come back with "no pcmcia driver"  i checked synaptic and it was installed, so i re-installed it and it worked, but as i said, there is no modprobe.conf in /etc/  :confused:

---

### Post by moises73 on 2006-02-27
i found this link that might work, i haven't tried it yet

[http://ubuntuforums.org/showthread.php?t=49056]("http://ubuntuforums.org/showthread.php?t=49056")

---

