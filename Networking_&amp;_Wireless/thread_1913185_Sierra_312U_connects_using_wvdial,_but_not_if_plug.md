---
title: "Sierra 312U connects using wvdial, but not if plugged in during boot"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by Mark F on 2012-01-22
Due to Network Manager not connecting this modem automatically in Kubuntu 11.10, I decided to try alternative means to get the modem to connect on boot.I have managed to get wvdial to connect it to the net - works beautifully! 

The problem I have is that if the modem is attached to the computer on login, wvdial complains thus:```
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyUSB2: Device or resource busy

```
If I unplug the modem, wait a few seconds then re-plug it, wvdial connects fine.
Kubuntu 11.10 doesn't apear to think it's a CD or anything.The (to me) relevant bits of dmesg indicates everything fine. I'm a bit lost now. Can anyone kindly tell me what to do next?

Thanks in advance
Mark

---

### Post by Mark F on 2012-01-23
Its amazing what a nights sleep does to the thought processes. Here's how I fixed it:

in /etc/network/interfaces I added:

```
auto ppp0
iface ppp0 inet wvdial
provider <insert wvdialler provider name>


```

---

