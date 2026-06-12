---
title: "Help with TV card"
date: 2009-11-23
forum: Multimedia Software
---

### Post by Red Khan on 2009-11-23
Hello, everybody!
Can't get my Avermedia AverTV Studio 303 to work.
Here is lspci output:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

```

---

### Post by Red Khan on 2009-11-29
Well, I figured it out myself. Posting this in case it might help somebody else.
In command line run the following:
```
sudo gedit /etc/modprobe.d/cx88xx 
```
In the opened file type this:
```
options cx88xx card=6 tuner=38
```
If you have another card and tuner use [this list]("http://ubuntuforums.org/showthread.php?t=1208233") to find an appropriate number.
You can find out what tuner you have by looking at the card. In my case it was a big box at the top of the card, it's number was printed right on it.
There was also problem with gnomeradio on 9.10 The solution is [here]("https://bugs.launchpad.net/ubuntu/+source/gnomeradio/+bug/422696/comments/15").
It works now, although now it has problems working together with my webcam.

---

