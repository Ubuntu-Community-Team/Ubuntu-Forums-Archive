---
title: "Syntax? Please help me generate a line for modprobe/options"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by seventyeights on 2009-01-11
I am trying to enable networking on an HP-E mini pc with an integrated 3com 3c905C network adapter. I am using a new installation of ubuntu intrepid.

It tries to connect, but fails and the applet just shows an exclamation point.

After researching, I've found that Autonegotiate is likely turned off by default (windows works ok because it overides this somehow).

Some people have reported enabling Autonegotiate by running a program called 3c90xCFG.exe.   I tried this both in windows, and off a live cd under wine. Neither worked, it's made for dos and it just dies.

Then I discovered this website describing options for the driver:
[http://www.mjmwired.net/kernel/Documentation/networking/vortex.txt](http://www.mjmwired.net/kernel/Documentation/networking/vortex.txt)
(lines 44 and 108 are relevant to me) 

I tried a command like "Modprobe 3c905C options=0x208" but when I do this, modprobe says that module isn't there.

Please help me generate a line in modprobe.d/options that I can try in order to set up autonegotiate.  I am very confused by the required syntax. 

Thanks.

---

