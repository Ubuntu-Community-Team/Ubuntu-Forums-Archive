---
title: "tv"
date: 2008-09-29
forum: Multimedia Software
---

### Post by atomo133 on 2008-09-29
hi
i ve got a kworld tv-pvr 878 (tv , fm , remote)..
but i can t watch tv...
how can i configure it??
are there any drivers??

---

### Post by mindoms on 2008-09-29
I dont use a analogue tv-card, but ill try to help anyway

first of all. lets see if your card was installed
```
ls -l /dev/video*
```
plese post the output

if this findes something, then you might just try:
```
sudo apt-get install xawtv
xawtv
```

try switching the channels, until you find one with a signal. (depends on your regeion and if you use terrestrial or cable tv)

EDIT:
use arrow up/down to switch channels.

hth, stefan

---

### Post by atomo133 on 2008-09-29
> **mindoms said:**
> I dont use a analogue tv-card, but ill try to help anyway

first of all. lets see if your card was installed
```
ls -l /dev/video*
```
plese post the output



atomo@atomo-desktop:~$ ls -l /dev/video*
ls: cannot access /dev/video*: No such file or directory

---

### Post by mindoms on 2008-09-29
so it is not yet installed. lets fetch some more information
```

uname -r
lsb_release -d
lspci
dmesg | grep video 

```

---

### Post by atomo133 on 2008-09-29
atomo@atomo-desktop:~$ uname -r
2.6.24-19-generic

atomo@atomo-desktop:~$ lsb_release -d
Description:	Ubuntu 8.04.1

atomo@atomo-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:07.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)

atomo@atomo-desktop:~$ dmesg | grep video
[   31.226878] Boot video device is 0000:01:00.0
[   45.015852] Linux video capture interface: v2.00

---

### Post by mindoms on 2008-09-29
I hope im not wasting your time, but you could try the following:
if
```
grep v4l /etc/X11/xorg.conf
```
doesnt print anything like
load "v4l"
then make a backup of your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_v4l
```

open the file
```
sudo gedit /etc/X11/xorg.conf
```

find the Section "MODULE" and insert the line:
```

	Load		"v4l"

```
if this section doesnt exist, create it.
mine looks like this. you may have more or less lines.
```

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

```
now reboot.
------------
if your X-server doesnt start as it should (no window-manager, just comand-line, or messy grafics) hit
ctrl + alt + F1
login, and run
```
sudo cp /etc/X11/xorg.conf_v4l /etc/X11/xorg.conf
```
then
```
sudo reboot
```
------------
otherwise run these commands.
```

ls -l /dev/video*
dmesg | tail -n 30

```
and post the output

hth, stefan

---

### Post by atomo133 on 2008-10-18
sorry it took so long to respond... i was kinda busy..

i did what you said and this the output

atomo@atomo-desktop:~$ ls -l /dev/video*
ls: cannot access /dev/video*: No such file or directory


atomo@atomo-desktop:~$ dmesg | tail -n 30
[   49.090294] Adding 514040k swap on /dev/sda3.  Priority:-1 extents:1 across:514040k
[   49.650802] EXT3 FS on sda2, internal journal
[   51.276681] ip_tables: (C) 2000-2006 Netfilter Core Team
[   51.681204] No dock devices found.
[   53.184565] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   53.184573] apm: disabled - APM is not SMP safe.
[   53.331826] ppdev: user-space parallel port driver
[   53.630930] audit(1224330852.728:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5114 profile="/usr/sbin/cupsd" namespace="default"
[   55.862359] eth0:  setting half-duplex.
[   58.169817] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   58.169835] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   58.169868] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   59.825256] NET: Registered protocol family 10
[   59.825808] lo: Disabled Privacy Extensions
[   59.826691] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   59.827731] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   99.357914] NET: Registered protocol family 17
[  100.621885] wlan0: Initial auth_alg=0
[  100.621897] wlan0: authenticate with AP 00:1a:4f:20:0b:b1
[  100.623672] wlan0: RX authentication from 00:1a:4f:20:0b:b1 (alg=0 transaction=2 status=0)
[  100.623682] wlan0: authenticated
[  100.623687] wlan0: associate with AP 00:1a:4f:20:0b:b1
[  100.632779] wlan0: RX AssocResp from 00:1a:4f:20:0b:b1 (capab=0x411 status=0 aid=1)
[  100.632788] wlan0: associated
[  100.632864] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  100.632870] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  100.632874] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  100.632878] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  100.634497] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  116.379272] wlan0: no IPv6 routers present

---

### Post by atomo133 on 2008-10-21
any ideas...
help please

---

### Post by atomo133 on 2008-10-26
i found some links  that seem useful , but i haven t accomplished anything yet....
any help would be appreciated

[http://bttv-v4l2.sourceforge.net/](http://bttv-v4l2.sourceforge.net/)

[http://ubuntuforums.org/showthread.php?t=32371](http://ubuntuforums.org/showthread.php?t=32371)

[http://www.linuxtv.org/wiki/index.php/Brooktree_Bt878](http://www.linuxtv.org/wiki/index.php/Brooktree_Bt878)

---

### Post by atomo133 on 2008-10-29
according to theses sites IT IS possible to use my tv-card onlinux
i just don t know how...
is there anyone who can help me out?

---

### Post by atomo133 on 2008-10-30
come on..
its the last thing that s keeping me from switching completely to ubuntu from windows

---

### Post by atomo133 on 2008-11-01
maybe should i try ubuntu 8.10???
do they have any new drivers that may help me fix the problem??

---

### Post by atomo133 on 2008-12-07
i have now a new installation xubuntu 8.10

when i try to scan i get this :

atomo@atomo-desktop:~$ sudo scanimage -L
[sudo] password for atomo: 
device `v4l:/dev/video0' is a Noname BT878 video (Jetway TV/Capture  virtual device


does this help at all?
am i closer to using this TV card??

---

### Post by atomo133 on 2008-12-08
too difficult ?

---

### Post by wolfen69 on 2008-12-08
try using vlc to watch tv. go to file>open capture device>video4linux tab>OK. let us know how it goes.

---

### Post by atomo133 on 2008-12-10
video4linux does nothing
but video4linux2 gives a strange image like it works but it s not tuned properly
how do i tune via vlc ?

---

