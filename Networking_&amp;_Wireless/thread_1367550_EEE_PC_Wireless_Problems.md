---
title: "EEE PC Wireless Problems"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by WRyder on 2009-12-29
So, I installed Ubuntu on my EEE PC, but the wireless won't work. I even tried plugging in an ethrnet cord into the computer, and that didn't work either! By the way, the computer is an EEE PC 900HD. 

Please help!

---

### Post by The Toxic Mite on 2009-12-30
Hey!

Can you go to Applications > Accessories > Terminal, and enter the following commands:

```

sudo lshw -c network
lspci -v less
iwconfig
ifconfig

```

Paste the outputs here when done :)

-TTM-

---

### Post by jml on 2009-12-30
I don't own a 900HD, but I do own a 900HA and I believe that they have the same wireless card.  When I decided to remove Windows and install a Linux distro on my HA, I discovered that not many distros supported the wireless card.  I have found that distros specifically designed for netbooks have better suppport for the wireless card.  Choices include Ubuntu NBR, (NetBookRelease,) EasyPeasy, EeeBuntu (not associated with Ubuntu.)

I am currently using Eeebuntu Standard,version 2.0.  It's not the latest release, but it serves my needs well and I get excellent wireless performance with it.  Version 4.0 is scheduled to be released in Feb. 2010 and it will be based on Debian rather than Ubuntu.

If you have access to a USB optical drive, you could download and burn a few different distros run them as a live CD and see if they support your 900HD any better than Ubuntu.

Joe

Joe

---

