---
title: "Broadcom wireless - poor scanning problem - odd?"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by anandamide on 2010-10-29
OK, so I have two wireless interfaces. The Gutsy upgrade borked my internal card (Broadcom b43 - wlan0) and after much faffing around I gave in and got a USB stick which works fine.

However, I'm now wanting to use my internal card - partly because I don't like having something useless in my desktop, and partly because I'd like to learn a bit more about linux and wireless / networking and this is a good place to start.

I have installed the b43 proprietary driver. This apparently installed without hiccup, although I noted a sticky thread giving a solution to a meerkat problem and also implemented that - no change.

All any scan brings up is a single access point (not mine). I live in a tower block in central London, a place swarming with wifi. Wlan1 picks up 6 no problem (including, fortunately, my own).

What could be going wrong here?

Here's the nitty gritty (note: I set iwconfig to ESSID:"MyNetName" while trying to sort this yesterday. hence the association!):

```
lspci:
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

iwconfig:
wlan0     IEEE 802.11bg  ESSID:"MyNetName"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

lsmod |grep b43:
b43                   187931  0 
mac80211              266657  3 b43,rt2x00usb,rt2x00lib
cfg80211              170293  3 b43,rt2x00lib,mac80211
led_class               3393  2 b43,rt2x00lib
ssb                    46169  1 b43

[    1.349515] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.768119] b43-phy2: Broadcom 4318 WLAN found (core revision 9)
[   13.013388] Registered led device: b43-phy2::tx
[   13.013408] Registered led device: b43-phy2::rx
[   13.013425] Registered led device: b43-phy2::assoc
[   13.013441] Registered led device: b43-phy2::radio
[   13.841360] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)

lshw -C network:
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1d:60:eb:97:c8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


iwlist scan:
wlan0     No scan results

lsb_release -d:
Ubuntu 10.10

uname -mr:
2.6.35-22-generic x86_64

```   

I've only included info for wlan0 as wlan1 is working fine. If info on both devices would be useful, just ask.

I'd rather get this sorted with the drivers as-is and not resort to ndiswrapper. The fact one access point is detected makes me think this could be fixed (am I being naive?).

Any help greatly appreciated. This isn't super-urgent but I would like to get it fixed and not sure where to start.

Cheers

---

### Post by anandamide on 2010-10-30
Bump :-)

---

### Post by klemes on 2010-10-30
Can't make many recomendations on this except maybe that this could be a hardware failure related problem.We should also consider this case.
An other thing is that I would definately try the Broadcom STA driver as I think it's suited better in noisy environments.

---

