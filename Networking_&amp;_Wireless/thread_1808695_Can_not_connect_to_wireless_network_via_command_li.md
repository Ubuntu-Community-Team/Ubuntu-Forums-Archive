---
title: "Can not connect to wireless network via command line in Ubuntu 11.04"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by Chenxicali on 2011-07-20
nm-applet works well on my Ubuntu 11.04. But fail to connect to wireless network connection via command lines after kill nm-applet.

The following is what I have tried in sequence:

1) iwconfig

wlan0 IEEE 802.11abgn ESSID:off/any Mode:Managed Access Point: Not-Associated

2) sudo iwlist wlan0 config

show the details of all the available wireless network

3) sudo iwconfig wlan0 ESSID NetworkID

The network I tried to connect did not require keys. At this moment, no network connection yet.

4) sudo dhclient wlan0

no response from the terminal, no connection either.

After the four steps, running iwconfig showed the same thing as 1).

Do not know where and how to find the problem. Any help is welcome!

---

### Post by chili555 on 2011-07-21
> Can not connect to wireless network via command line in Ubuntu 11.04...and without some extraordinary measures, you probably never will. Killing nm-applet simply kills the little icon on your desktop. The underlying application Network Manager is still alive and well and in firm control of your wireless and wired interface. Even if you remove it as a start-up program, it often re-spawns anyway. Of course, you could simply uninstall it. You may be able to remove it from being activated by rc.d without removing it.

But why? If NM is working well, why fight momentum? Are you trying to set up a server or similar that will run without a desktop environment? Are you just trying to have the old-school command-line experience? By the way, I *love* the old-school command-line experience!

---

