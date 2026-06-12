---
title: "Wifi connection get's disconnected when downloading torrents"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by SixtyYen on 2012-11-25
Hello all,

after a few troubles with installing (had to deactivate my raid0 set up - grub2 boatloader wouldn't install) and my videocard's drivers, I now have a question where I have to resort to others to help solve it. I'm a newbie to Unix systems, so be easy on me ;) .

In any case, the problem is that downloading a torrent with the transmission client causes my wifi to lose connection. It's fine for normal downloads so I'm tempted to think it has to do with the number of connections. My wifi has always been a tad shaky and prone to losing connection, but it worked fine with Windows 7 to the point where I could at least use torrents and having the occasional disconnect (urban area, lot's of wifi's - I have already set the wifi router to the best possible channel). I do not have the possibility of a wired connection (student house).

I use an USB wifi system. Perhaps it's a driver issue, perhaps something far worse (I hope not). I'm using Ubuntu 12.10.

A few details:
.......:~$ sudo lshw -C network
[sudo] password for ...: 
  [B]*-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1.7
       logical name: wlan0
       serial: 00:87:12:26:08:88
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.5.0-18-generic firmware=N/A ip=192.168.1.10 link=yes multicast=yes wireless=IEEE 802.11bg[/B]

---

### Post by SixtyYen on 2012-11-25
Problem solved. Upgraded to Windows 8 - everything works now!

---

