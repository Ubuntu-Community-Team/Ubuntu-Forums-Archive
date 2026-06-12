---
title: "Acer Aspire 5315 - Major wireless issues"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by thequestioner on 2012-07-24
So after using windows my whole life, i switched to linux 2 days ago.  everything is running smoothly apart from the wireless (im confined to the downstairs part of my house atm with a LAN cable)

so my problems are as follows:

1: in the network part of the taskbar (top right), there isn't even an option for wireless networks, it's just wired.

2: when i did manage to see the wireless option, it would continuously tell me that the "network device is not ready: firmware missing"

Now i'm a complete noob on this as i've only been using this for about 2 days as i said, but i have spent quite a while browsing through forums and trying stuff out (madwifi, etc) and still nothing has worked.


any help on this issue, or anyone who also has the aspire 5135 and has managed to get it working?


any help is appreciated

---

### Post by cortman on 2012-07-24
Hi, what's the output of

```
lscpci
```

?

---

### Post by thequestioner on 2012-07-24
> **cortman said:**
> Hi, what's the output of

```
lscpci
```?

it would be:

```
orin@orin-Aspire-5315:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 
```

---

### Post by cortman on 2012-07-24
Looks like you have the Broadcom wireless card, which has been known to be problematic, but there appear to be several solutions [here]("http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working").

---

### Post by NikTh on 2012-07-24
Hi , 
try this 
```
sudo apt-get install linux-firmware-nonfree
``` 

reboot without etherent cable in , and see if wireless work.

Thanks

---

### Post by thequestioner on 2012-07-24
FIXED!

God knows how i didnt find these posts earlier. i used a combination of [Silambarasan]("http://askubuntu.com/users/10064/silambarasan")'s answer on [this]("http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working") post, and the helpful advice provided [here]("http://ubuntuforums.org/showthread.php?t=1873013&page=2"). thanks to the people who posted  :D as a complete beginner on linux and ubuntu i can gladly say that this helped alot :D

---

