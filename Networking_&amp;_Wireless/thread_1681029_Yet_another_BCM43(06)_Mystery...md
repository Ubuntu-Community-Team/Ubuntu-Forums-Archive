---
title: "Yet another BCM43(06) Mystery.."
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by Kegusa on 2011-02-03
Hiyas all, as title explains this is the dreaded broadcom 43XX series making an appearance here again. 

The problem is that the card is installed (fwcutter) and it plays nice sofar. It can even see the networks around with both nm-manager and wicd, but it cant connect to any router regardless of security. Tried no security, wep, wpa and all the channels on two different routers just to exclude a faulty router.

When it tries to connect it doesnt do much visually, but dmesg gives the following output about 8-10 times: 

> [ 6610.362143] wlan0: direct probe to 00:1c:f0:54:d1:f7 (try 1)
[ 6610.560032] wlan0: direct probe to 00:1c:f0:54:d1:f7 (try 2)
[ 6610.760044] wlan0: direct probe to 00:1c:f0:54:d1:f7 (try 3)
[ 6610.960153] wlan0: direct probe to 00:1c:f0:54:d1:f7 timed out
 

Some more info: 

> kenneth@kenneth-desktop:~$ lspci | grep Wireless
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


> kenneth@kenneth-desktop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0e:8e:00:2a:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


> kenneth@kenneth-desktop:~$ lsmod | grep b43
b43                   187932  0 
mac80211              267163  1 b43
cfg80211              170485  2 b43,mac80211
led_class               3393  1 b43
ssb                    46201  1 b43


Sometimes I might get this one from dmesg also: 

> [ 7046.620040] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 7046.791677] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7057.830023] eth0: no IPv6 routers present


Any Ideas are more than welcome, I'm out in the dark with this error, been trying for a day before I came here posting!

EDIT: Almost forgot to mention the distro and kernel! 

Ubuntu 10.10 64bit with 2.6.35-25-generic kernel.

---

### Post by hansolo4949 on 2011-02-03
Um, a problem with it may be the kernel version. Perhaps they removed some helpful code from the kernel for b43xx to cut down on the size? try using a livecd, and use the livecd way on my [forum post]("http://ubuntuforums.org/showthread.php?t=1660535"), more specifically [on this site]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers"). Hope that helps! Oh, and don't forget [this thread]("http://ubuntuforums.org/showthread.php?p=10425278#post10425278") I started for just this problem.

Hope it helps!

---

### Post by Kegusa on 2011-02-06
Strangest thing happened now. 

After all the error messages I've had from connecting to the wireless network I found out how to fix this. After looking at the b43 module using "modinfo b43" I found several options to this module. 

Since I dont have bluetooth on my machine I opted for disabling coexistence with bluetooth like this:

```
sudo modprobe -r b43
sudo modprobe b43 btcoex=0
```

And suddenly I was online, it seems that the coex flag was messing with my ability to connect to a WEP encrypted network.
Dmesg logs didnt indicate anything wrong with bluetooth so it was luck that made me try everything possible :p 

Anyone have an idea why the bluetooth coexistence mode should interfere like this? And is this a bug? Either way, it fixed the problem for me :D

---

### Post by hansolo4949 on 2011-02-06
Wiiieerrdddd.......I wonder why that happens. Yet another mystery lost to the ages....:p

---

### Post by Kegusa on 2011-02-06
Yeah, after I found out what the problem was I did a little search for it and found another thread.

[http://forums.opensuse.org/english/get-technical-help-here/wireless/428611-suse-11-2-broadcom-scan-fails-find-wireless-net-2.html](http://forums.opensuse.org/english/get-technical-help-here/wireless/428611-suse-11-2-broadcom-scan-fails-find-wireless-net-2.html)

It seems that a few of the 14e4:4320 (rev 03) cards have this error and ofcourse I had one. Some other thread I found about the same problem they actually had a bit of paper on some pins on the wirelesscard to prevent btcoex physically. o.O 

Something about the lpphy bcmwl bluetooth thing is causing this, and sofar as I've found there is no absolute fix as of this date. 

Think I'll send a little message to the ubuntuwiki and notifying them of this b43 issue on this specific card.

---

