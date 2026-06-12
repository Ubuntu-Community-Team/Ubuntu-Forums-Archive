---
title: "Upgraded 9.10 cant enable wireless"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by Nottaken on 2009-11-02
Ever since i upgrade to 9.10 from 9.04 I have not been able to enable wireless. In the nw-applet I cant toggle the "enable wireless" radio button.  a similiar issue seems to have been described at:
[http://ubuntuforums.org/showthread.php?t=1284505](http://ubuntuforums.org/showthread.php?t=1284505)

---

### Post by elmy on 2009-11-21
Hmmm,

This seems to happen frequently when upgrading.

Now hear my story.

I have TWO Hewlett Packard Compaq NC8000 Laptops.

The reason I have two was because I got sick of having to stuff around with the interfaces file everytime I upgraded and found the wifi would stop working. So I created a test machine and a production machine.

I upgraded my test machine from a 9.04 to 9.10 and the wireless is still working. I took that as a good indication to proceed with my production machine. Now both laptops are the same model. Both laptops were at the same software level (and upto date with the canonical updates).

I upgraded the second laptop and the enable wireless option doesn't even appear in the network manager menu. The connection settings are still in network manager under wireless. The /etc/network/interfaces files on both laptops are the same,but when I do an ifconfig and iwconfig I get different results.

there is no wlan0 in ifconfig on the production laptop but there is on my test laptop.  

When I do a hardware test using the System Testing tool,it detects that the Atheros wifi card exists.

So I wanna know why 1 NC8000 can upgrade okay,but the other one doesn't.

regards
elmy

---

