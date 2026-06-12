---
title: "Network Card Not working"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by Newusers on 2011-04-21
Hi I have BroadCom BCM4318 802.11B/G Wireless Card. When I first started Ubuntu a week ago it didn't work, but I fixed it after a day or two of googling it. However I made a mistake and uninstalled the Network Manager. I then reinstalled Ubuntu, but it wouldn't load the card again. I activated the driver, and restarted the computer, but then, since It was connected via Ethernet, it wouldn't reconize the Ethernet connection, but the wireless card it did, but wouldn't find a network that is supported. 

Help!

---

### Post by josephmills on 2011-04-21
> **Newusers said:**
> Hi I have BroadCom BCM4318 802.11B/G Wireless Card. When I first started Ubuntu a week ago it didn't work, but I fixed it after a day or two of googling it. However I made a mistake and uninstalled the Network Manager. I then reinstalled Ubuntu, but it wouldn't load the card again. I activated the driver, and restarted the computer, but then, since It was connected via Ethernet, it wouldn't reconize the Ethernet connection, but the wireless card it did, but wouldn't find a network that is supported. 

Help!

hi there could I please see a 
```

lspci -vnn | grep 14e4

``` 
Thanks

---

### Post by Newusers on 2011-04-22
> 05:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
That is the output.

---

### Post by josephmills on 2011-04-22
could I now see 
```

lsmod | grep b43

```
```

dmesg | grep b43

```
Thanks

---

### Post by Newusers on 2011-04-22
Results:
> 
**_*lsmod*_**
b43                   187964  0 
mac80211              267099  1 b43
cfg80211              170485  2 b43,mac80211
led_class               3393  1 b43
ssb                    46201  1 b43

_***dmesg***_

[    2.049787] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.295709] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   13.459619] Registered led device: b43-phy0::tx
[   13.459635] Registered led device: b43-phy0::rx
[   13.459657] Registered led device: b43-phy0::radio
[   15.060024] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)



---

### Post by josephmills on 2011-04-22
plug into a router then. If you go to **system-->addmin-->synaptic package manager.** After you enter your password please go to the search bar and type in bcmwl. make sure that **bcmwl modaliases** is installed. if not install.

---

### Post by Newusers on 2011-04-23
I checked Synaptic Package Manager, and it is installed, should I install "bcmwl-kernel-source"?

---

