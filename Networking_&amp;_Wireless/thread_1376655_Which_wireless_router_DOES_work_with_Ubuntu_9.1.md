---
title: "Which wireless router DOES work with Ubuntu 9.1?"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by pifactory on 2010-01-09
I have a linksys wrt54gl wireless router and am running Ubuntu 9.1 netbook remix. After many frustrating hours I am still no further forward trying to get connected to the internet.

It's going to be cheaper and quicker to get a wireless router that does work with Ubuntu.

Suggestions please? Thanks.

---

### Post by underquark on 2010-01-09
I didn't think the router even knew what OS was on the computer(s) connected to it. What wireless device is the computer using to try to connect to the router?

---

### Post by %hMa@?b&lt;C on 2010-01-09
I don't think the problem is on the router's side, but on yours.  What does 
```
sudo lshw -C network

```
output so that I can see what wifi card you have?

---

### Post by Grenage on 2010-01-09
Indeed, as far as the router is concerned, it's just a device requesting a DHCP lease (unless you are using static addresses).  If there is a problem it is almost certainly with your wireless configuration, or a driver/network manager.

---

### Post by pifactory on 2010-01-09
Thanks for this.

The wireless card is:

AR5001 Wireless Network Adapter

Atheros

The machine is an Eeepc running celeron processor

Does this help? Thanks.

---

### Post by %hMa@?b&lt;C on 2010-01-09
you need madwifi drivers for that
[http://art.ubuntuforums.org/showthread.php?t=1163380](http://art.ubuntuforums.org/showthread.php?t=1163380)
edit: 1000 posts! :P

---

### Post by Leppie on 2010-01-09
i am using the wrt54g with ubuntu ;)
works fine for me :)

---

### Post by sanderj on 2010-01-10
> **jeffc313 said:**
> you need madwifi drivers for that
[http://art.ubuntuforums.org/showthread.php?t=1163380](http://art.ubuntuforums.org/showthread.php?t=1163380)
edit: 1000 posts! :P

FYI: My Samsung NC-10 apparently has the Athereos AR5001 (see below), and that just works out of the box using plain Ubuntu 9.10. 
So the good news for the OP is that he doesn't need any kind of driver hacking...


```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

---

### Post by %hMa@?b&lt;C on 2010-01-10
> **sanderj said:**
> FYI: My Samsung NC-10 apparently has the Athereos AR5001 (see below), and that just works out of the box using plain Ubuntu 9.10. 
So the good news for the OP is that he doesn't need any kind of driver hacking...


```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

that's funny, because my brother's laptop has the same exact chipset
```
04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```
and it works with ath_pci (madwifi) but not ath5k

---

### Post by sanderj on 2010-01-10
Maybe this is helpful:

```
sander@quirinius:~$ lsmod | grep ath
ath5k                 124580  0 
mac80211              181076  1 ath5k
led_class               4096  1 ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
sander@quirinius:~$ 
```

 
So, does this mean I use the native driver? 
FYI 1: it works perfect
FYI 2: I haven't done anything by hand; everything worked out of the box.

---

### Post by %hMa@?b&lt;C on 2010-01-10
that is funny.  I did a dist-upgrade here, so that could be the issue, but still I don't see why ath5k doesn't work.  I'm using ath_pci and it works fine, but with ath5k, I couldn't connect to any networks.  I could see them, but not access.  
```
david@celeron:~$ lsmod |grep ath
ath_pci                92284  0 
ath_rate_sample        11932  1 
wlan                  198704  5 ath_pci,wlan_wep,wlan_scan_sta,ath_rate_sample
ath_hal               192272  3 ath_pci,ath_rate_sample

```

---

