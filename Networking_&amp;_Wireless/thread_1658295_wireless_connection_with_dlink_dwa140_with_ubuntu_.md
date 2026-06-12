---
title: "wireless connection with dlink dwa140 with ubuntu 10.10"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by hugues72 on 2011-01-02
hello, 
i have just installed ubuntu 10.10 and i am trying to connect to internet with my wireless connection with a usb key dlink dwa140 driver rt2800usb
it works for a few seconds, then stops. i need to re-start the pc to get it work again for a few seconds then it stops.
what should i do to configure it properly?
many thx
hugues

---

### Post by Liquid2006 on 2011-01-13
Hi there, I had the same symptoms as you. Turns out it was two drivers fighting to get control of the dongle.

If you do: lsmod | grep rt
You'll see there is a rt2870 module loaded along with some rt2x00usb and rt2800usb. What a mess.

I just added these lines to my /etc/modprobe.d/blacklist.conf

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

That's it...I think. I'm yet to reboot and see if the correct module loads by itself.
You can do the following to load it though:
sudo modprobe rt2870sta

Hope that helps.
Tim

---

