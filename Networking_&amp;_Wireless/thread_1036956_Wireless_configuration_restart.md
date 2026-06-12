---
title: "Wireless configuration restart"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by Sprut1 on 2009-01-11
Lately I've run into some issues concerning my wireless network. It do work and I'm using it now, but when I put an interface in monitor mode (to work with the aircrack-ng tools) wireless is obviously brought down. When I need to access the internet again I simply destroy the interface and bring up another in Managed mode, but it constantly gets stuck at "Configuring device" when I try to connect to a network.

I've tried
```
sudo /etc/init.d/networking restart
```
What exactly happens then? Is it restarting networking and preparing it again according to "/etc/network/interfaces"? Or is it only "ifup -a" that uses the interfaces configuration?

Also, in KNetworkManager, does anyone know what happens when you use "Disable/Enable Wireless" and "Switch to offline/online mode"? Is that the same as "ifup -a"?

And lastly, sometimes when I have been adding/removing interfaces and fiddling with my wireless for quite some time I often suddenly get "ioctl({something}): Input/output error" when I try to use a command like:
```
sudo wlanconfig ath0 create wlandev wifi0
```
which normally works perfectly, what is causing the input/output error? Destroying the interface is never a problem.

Any suggestion that'll enhance my knowledge is very appricated! Cheers!

---

