---
title: "Wireless without a card"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by BurnChao on 2009-01-23
I know this is silly, but the NetworkManager tells me of at least 8 different wireless networks it's found that I could connect to (in addition to the wired one I'm using). Two of them don't require passwords, the rest do. When I try using the ones without passwords, I can't get on, which makes sense, since...

I don't have a wireless card.

How is it finding these wireless networks? This is crazy, right? The only thing I could think of is my Nintendo Wifi connection hub. (a device to allow the Wii and DS to connect to the internet via my computer) Could it be that? Or what's going on?

---

### Post by wirelessmonkey on 2009-01-23
Easy enough to find out... from terminal, post the output of: ```
iwconfig
```

---

### Post by BurnChao on 2009-01-23
Okay, here's the output:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"06B403333987"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by wirelessmonkey on 2009-01-23
Well, I suspect you are correct.  wlan0 is a wireless device with a driver and valid config... neat!

---

### Post by zenial on 2009-01-23
WOW THATS DOPE:o

---

### Post by Ayuthia on 2009-01-24
Can you post the results of lspci -nn and lsusb?  It might help identify the card.

---

### Post by BurnChao on 2009-01-24
Sure. lspci -nn is :

```
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV380 [Radeon X600 (PCIE)] [1002:5b62]
01:00.1 Display controller [0380]: ATI Technologies Inc RV380 [Radeon X600] [1002:5b72]
03:03.0 Modem [0703]: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI [8086:1080] (rev 04)
03:08.0 Ethernet controller [0200]: Intel Corporation 82801G (ICH7 Family) LAN Controller [8086:27dc] (rev 01)
```

lsusb is:
```
Bus 005 Device 008: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 005 Device 007: ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 WebCam
Bus 005 Device 009: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 005 Device 006: ID 0411:008b MelCo., Inc. Nintendo Wi-Fi
Bus 005 Device 004: ID 0d49:7310 Maxtor 
Bus 005 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 002: ID 0bc2:0502 Seagate RSS LLC 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:5112 Dell Computer Corp. Photo AIO Printer 924
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by Ayuthia on 2009-01-24
> **BurnChao said:**
> 
lsusb is:
```
Bus 005 Device 006: ID 0411:008b MelCo., Inc. Nintendo Wi-Fi

```

It is the only device that I could see that could be scanning for wireless sites.  Doing a quick search, it looks like it uses a ralink module (rt2500usb).  So it could be possible that you can connect with this module or possibly use one from serialmonkey.

So it does look like your thoughts were correct!

---

### Post by BurnChao on 2009-01-24
So, since it's supposed to function as an antenna, allowing Nintendo hardware to use my computer as a router to the net, that makes my wonder: Am I seeing a list of wireless networks I can connect to, or am I seeing a list of wireless computers that I am routing?

---

### Post by wirelessmonkey on 2009-01-25
you are seeing a list of wireless networks that can be connected to..., you are 'routing' nothing.

---

### Post by BurnChao on 2009-01-26
Thanks for the responses.

I also just realized an obvious way I can figure out more. Unplug the doo-dad. That's should make it obvious whether or not it's responsible.

If I can log onto one without a password (I haven't been able to yet), would I be able to use it along with my wired connection, boosting my speeds? Internet in parallel?

---

