---
title: "tvtime no signal"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by gu014 on 2006-06-14
Hello,
I am having some problems getting tvtime to work on my ubuntu 6.06.  I have a Emuzed TVT3 Dual TV Tuner.  Here is the result of a lspci:

0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub
0000:00:01.0 PCI bridge: Intel Corporation 945G/P PCI Express Graphics Port
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
0000:00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 0106: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
0000:05:04.0 Multimedia video controller: NEC Corporation: Unknown device 013a (rev 0b)
0000:05:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)



Here is the relative output of dmesg:
[4296221.623000] Linux video capture interface: v1.00
[4296221.663000] bttv: driver version 0.9.16 loaded
[4296221.663000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4296253.051000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4296253.079000] saa7134 ALSA driver for DMA sound loaded
[4296253.079000] saa7134 ALSA: no saa7134 cards found


When i load tvtime i receive no signal.  Can anyone please direct me to resolve this issue? Thank you very much.

---

### Post by fragos on 2006-06-15
The most likely problem with bttv is identification of the tuner.  You may find that tuner is set to 0.  If so take out the TVcard and look on the large packages on the board.  You may have to remove the card vendor's sticker to see the tuner brand.  With that you can get to a tuner number to configure.  SuSE was like that for my WinTV GO but Ubuntu did identify it correctly.

---

### Post by ersplus on 2006-06-16
On term (sorry for my english)

Maybe compile the last v4l release solve your pbs

```
sudo apt-get install mercurial build-essential
sudo apt-get build-dep xserver-xorg-driver-v4l
```

Get the last sources of v4l
```
hg clone http://linuxtv.org/hg/~mrechberger/v4l-dvb
```

```
cd v4l-dvb
cd v4l
```

compil and install :

```
make
sudo make install/[code]

[code]tvtime --device=/dev/video0 -S
```

or

```
tvtime --device=/dev/video1 -S
```

Then the device will work

---

