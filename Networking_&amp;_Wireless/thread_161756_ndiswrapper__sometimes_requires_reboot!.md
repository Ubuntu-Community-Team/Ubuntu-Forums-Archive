---
title: "ndiswrapper:  sometimes requires reboot!?"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by m0nstr42 on 2006-04-17
My wireless card (Broadcom/Dell Truemobile 1300) works (for the most part) just fine using ndiswrapper, if I stay in one spot.  Whenever I go to another location (e.g. home to campus/work), I shut down the laptop (don't have suspend/hibernate working yet), then reboot when I get there.  I've taken to manually bringing things up to be able to connect to whatever network is around, so I go with

```
sudo modprobe ndiswrapper
sudo iwconfig wlan0 essid "whatevernetwork"
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

The problem is this only works about half of the time.  A lot of times I will either get no connectivity to the network (which is working just fine for other computers on it), or it connects and dhclient sits there broadcasting a request (it sometimes even sees a NAK that it just seems to ignore).  When this happens, about 90% of the time I can make the problem go away by rebooting.  Removing and re-inserting the module with rmmod then modprobe doesn't seem to work.

I'd love to know some way to make fix this problem so that it works every time.  I'd even settle for some way to force a reset without a reboot.

---

### Post by m0nstr42 on 2006-04-19
I may have a solution.  Check out [this related post]("http://ubuntuforums.org/showthread.php?p=936192#post936192").

---

