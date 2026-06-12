---
title: "another windows user cant connect with ubuntu"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by arionadouble on 2008-12-28
Atheros network adapter on a wireless desktop. Linksys router wpa personal. how can i configure the connection in ubuntu.  a process would really be helpful im using a dual boot.:confused:

---

### Post by pytheas22 on 2008-12-28
Please post the output of these commands:
```

sudo iwlist scan
lspci -nn
lshw -C Network
uname -rm
```

---

### Post by arionadouble on 2008-12-29
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
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
01:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR5413 802.11abg NIC [168c:001b] (rev 01)
01:05.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k Data/Fax Modem [14f1:2f20]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
04:00.0 VGA compatible controller [0300]: nVidia Corporation G72 [GeForce 7500 LE] [10de:01dd] (rev a1)

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:c1:35:2f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:01:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 42:ad:a6:c7:02:ea
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

2.6.27-7-generic x86_64

---

### Post by pytheas22 on 2008-12-29
hmmm, according to the madwifi site, this card should be supported.  I wonder if the ath_pci driver is just not loading for some reason.  Could you please post the output of:
```

sudo modprobe ath_pci
dmesg | grep -e ath
modinfo ath_pci
```

It's possible that the version of madwifi that ships with Ubuntu 8.10 is too old to support this card, in which case we can just compile a new version.  But 8.10 was released only a couple months ago so it should be pretty up-to-date...

---

### Post by arionadouble on 2008-12-29
yes i can please give me a couple minutes and is that an l in 
dmesg ? grep -e ath

---

### Post by melojo on 2008-12-29
> **arionadouble said:**
> yes i can please give me a couple minutes and is that an l in 
dmesg ? grep -e ath

That is not an l its called a pipe

Also known as a vertical bar, the pipe is a computer keyboard key ( | ) that is two vertical lines above one another and commonly looks like a full vertical line. This symbol is commonly found on the same United States qwerty  keyboard key as the back slash key.

you can do a search on google to find out more.

---

### Post by arionadouble on 2008-12-29
arion@ubuntu:~$ sudo modprobe ath_pci
arion@ubuntu:~$ dmesg | grep -e ath
[   10.182539] ath_hal: module license 'Proprietary' taints kernel.
[   10.191637] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   10.272445] ath_pci: 0.9.4
[   10.272491] ath_pci 0000:01:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.272950] ath_pci 0000:01:04.0: PCI INT A disabled
arion@ubuntu:~$ modinfo ath_pci
filename:       /lib/modules/2.6.27-7-generic/volatile/ath_pci.ko
srcversion:     D3FD3BD11169A96DBCFF8DE
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.27-7-generic SMP mod_unload modversions 
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)
arion@ubuntu:~$

---

### Post by arionadouble on 2008-12-29
any idea from this nfo
:confused:

---

### Post by pytheas22 on 2008-12-29
Do you have a switch (or a key combination, like function+F2) to enable/disable radio on this card?  If so, please try flipping it, then wait a few seconds and see if the wireless appears.

In the meantime I'll google around and see if I can find anything.  I may not be able to respond again till tomorrow, however.

EDIT: please also post the output of this; I think it may help:

```
sudo rmmod ath_pci
sudo modprobe ath9k
lshw -C Network
dmesg | grep -e ath
```

---

### Post by arionadouble on 2008-12-30
arion@ubuntu:~$ sudo rmmod ath-pci
ERROR: Module ath_pci does not exist in /proc/modules
arion@ubuntu:~$ sudo modprobe ath9k
arion@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:c1:35:2f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:01:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: f2:71:a2:21:7f:ea
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
arion@ubuntu:~$ dmesg | grep -e ath
[   11.040052] ath_hal: module license 'Proprietary' taints kernel.
[   11.094000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   11.137038] ath_pci: 0.9.4
[   11.137089] ath_pci 0000:01:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.137577] ath_pci 0000:01:04.0: PCI INT A disabled
[  157.385554] ath_pci: driver unloaded
[  239.079974] ath9k: 0.1
arion@ubuntu:~$ 

thats all igot i dont know about the first entry i may have typed something in wrong while in the terminal cause it brought up an error

---

### Post by arionadouble on 2008-12-30
oh yes and i know of no kind of switch and just to confirm i looked into a switch and found nothing.  i have a desktop just to be clear.

---

### Post by pytheas22 on 2008-12-30
Yes, you typed the name of the module a bit incorrectly--'ath_pci' has an underscore ( _ ), not a hyphen ( - ).  Please run these commands and post the output:
```

sudo rmmod ath_pci
sudo modprobe ath9k
dmesg | grep -e ath
```

---

### Post by arionadouble on 2008-12-31
its still bringn up an error when i type
sudo rmmod ath_pci

---

### Post by pytheas22 on 2008-12-31
What does the error message say?

---

### Post by arionadouble on 2009-01-01
arion@ubuntu:~$ sudo rmmod ath_pci
[sudo] password for arion: 
arion@ubuntu:~$ sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules
arion@ubuntu:~$ sudo modprobe ath9k
arion@ubuntu:~$ dmesg | grep -e ath
[   10.051263] ath_hal: module license 'Proprietary' taints kernel.
[   10.056076] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   10.090151] ath_pci: 0.9.4
[   10.090207] ath_pci 0000:01:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.090684] ath_pci 0000:01:04.0: PCI INT A disabled
[  107.466510] ath_pci: driver unloaded
[  137.565955] ath9k: 0.1
arion@ubuntu:~$ 

this is what im getting

---

### Post by arionadouble on 2009-01-01
so should i try opening ndiwrapper or go a different route i have no clue what is causing this i thought for sure the os would function properly out of the box but as a first timer i need a general way to approach this problem

---

### Post by pytheas22 on 2009-01-01
It seems that ath9k doesn't want to work any better than ath_pci.  In that case, let's try ndiswrapper.  Please run these commands to try ndiswrapper (please post all output):
```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip
unzip WLan*
cd 802BGA
sudo ndiswrapper -i netathr.inf
sudo rmmod ath9k
sudo rmmod ath_pci
sudo rmmod ath5k
sudo depmod -a
sudo modprobe ndiswrapper
ndiswrapper -l
sudo iwlist scan
dmesg | grep -e ndis -e wlan
pwd
```

Please post all output so that I can verify that things go as planned.  Hopefully, by the end of these commands, your wireless will be working.

---

### Post by arionadouble on 2009-01-01
arion@ubuntu:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils:1.9 wget [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA) unzip WLan*
[sudo] password for arion: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
arion@ubuntu:~$  sudo apt-get install ndiswrapper-common ndiswrapper-utils:1.9 wget [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA) unzip WLan*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
arion@ubuntu:~$ sudo apt-get install ndiswrapper_common ndiswrapper-utils:1.9 wget [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA) unzip WLan*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper_common
arion@ubuntu:~$ cd 802BGA
bash: cd: 802BGA: No such file or directory
arion@ubuntu:~$ sudo ndiswrapper -i netathr.inf
sudo: ndiswrapper: command not found
arion@ubuntu:~$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
arion@ubuntu:~$ sudo rmmod ath_pci
arion@ubuntu:~$ sudo rmmod ath5k
ERROR: Module ath5k does not exist in /proc/modules
arion@ubuntu:~$ sudo depmod -a 
sudo modarion@ubuntu:~$ sudo modprobe ndiswrapper
arion@ubuntu:~$ ndiswrapper -1
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
arion@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

arion@ubuntu:~$ dmesg | grep -e ndis -e wlan 
[   10.450322] wlan: 0.9.4
[  508.004854] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  508.014272] usbcore: registered new interface driver ndiswrapper
arion@ubuntu:~$ pwd
/home/arion
arion@ubuntu:~$ 

and im assuming i did something wrong

---

### Post by melojo on 2009-01-01
type each line separately and try again making sure it is correct.

I will try and help make sure you typed it in correctley until pytheas22 gets back to you.

---

### Post by arionadouble on 2009-01-02
if i did 
maybe this
pwd

[sudo] password for arion: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
arion@ubuntu:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
arion@ubuntu:~$ 
arion@ubuntu:~$ wget [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip)
--2009-01-01 23:47:22--  [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip)
           => `WLan Driver 802BGA.zip'
Resolving ftp.work.acer-euro.com... failed: Name or service not known.
wget: unable to resolve host address `ftp.work.acer-euro.com'
arion@ubuntu:~$ 
arion@ubuntu:~$ unzip WLan*cd 802BGA
unzip:  cannot find or open WLan*cd, WLan*cd.zip or WLan*cd.ZIP.

No zipfiles found.
arion@ubuntu:~$ sudo ndiswrapper -i netathr.inf
sudo: ndiswrapper: command not found
arion@ubuntu:~$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
arion@ubuntu:~$ sudo rmmod ath_pci
arion@ubuntu:~$ sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules
arion@ubuntu:~$ sudo depmod -a
arion@ubuntu:~$ sudo modprobe ndiswrapper
arion@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
arion@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

arion@ubuntu:~$ dmesg | grep -e ndis -e wlan
[   10.161020] wlan: 0.9.4
[  493.276937] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  493.285498] usbcore: registered new interface driver ndiswrapper
arion@ubuntu:~$ pwd
/home/arion
arion@ubuntu:~$ 

im crossing my fingers

---

### Post by melojo on 2009-01-02
type 
```
sudo apt-get update
```

try again

---

### Post by arionadouble on 2009-01-02
[sudo] password for arion: 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
arion@ubuntu:~$

and then..... no and then!!! 
i have to find a little humor amongst my defeats

---

### Post by melojo on 2009-01-02
seems like nothing is going to be easy on you.  Be patient its usually not this hard.

can you post the contents of the file

/etc/apt/sources.list

---

### Post by melojo on 2009-01-02
Also can you post the contents of /etc/hosts

and type this in a terminal

```
ping www.google.com 
```

let it go for 4 lines and then hit ctl + c  to stop it and post the output

---

### Post by pytheas22 on 2009-01-02
It looks like you had no Internet connection when you tried installing ndiswrapper as per my instructions in my last post (sorry for not pointing out that you needed to be online).  Can you plug in via ethernet and try running these commands again:
```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip
unzip WLan*
cd 802BGA
sudo ndiswrapper -i netathr.inf
sudo rmmod ath9k
sudo rmmod ath_pci
sudo rmmod ath5k
sudo depmod -a
sudo modprobe ndiswrapper
ndiswrapper -l
sudo iwlist scan
dmesg | grep -e ndis -e wlan
pwd
```

If you have no way of getting online without wireless, let me know and we can work around that, although it will be extra work.

---

### Post by arionadouble on 2009-01-02
i would much rather just work around it if it can be done.  i have a ethernet connection but its in a different room of my place and kind of off limits at the moment.

---

### Post by arionadouble on 2009-01-02
arion@ubuntu:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
[sudo] password for arion: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
arion@ubuntu:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
arion@ubuntu:~$ 
arion@ubuntu:~$ wget [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip)
--2009-01-02 14:10:53--  [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip)
           => `WLan Driver 802BGA.zip'
Resolving ftp.work.acer-euro.com... 193.0.238.152
Connecting to ftp.work.acer-euro.com|193.0.238.152|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /notebook/ferrari_5000/vista/Drivers ... done.
==> SIZE WLan Driver 802BGA.zip ... 2689538
==> PASV ... done.    ==> RETR WLan Driver 802BGA.zip ... done.
Length: 2689538 (2.6M)

100%[======================================>] 2,689,538   15.9K/s   in 3m 38s  

2009-01-02 14:14:35 (12.1 KB/s) - `WLan Driver 802BGA.zip' saved [2689538]

arion@ubuntu:~$ 
arion@ubuntu:~$ unzip WLan*
Archive:  WLan Driver 802BGA.zip
   creating: 802BGA/
  inflating: 802BGA/athr.sys         
  inflating: 802BGA/athrext.cat      
  inflating: 802BGA/athrextx.cat     
  inflating: 802BGA/athrx.sys        
  inflating: 802BGA/data1.cab        
  inflating: 802BGA/data1.hdr        
  inflating: 802BGA/data2.cab        
  inflating: 802BGA/ISSetup.dll      
  inflating: 802BGA/layout.bin       
  inflating: 802BGA/netathr.inf      
  inflating: 802BGA/netathrx.inf     
  inflating: 802BGA/Notes.txt        
  inflating: 802BGA/setup.exe        
  inflating: 802BGA/setup.ini        
  inflating: 802BGA/setup.inx        
  inflating: 802BGA/setup.iss        
  inflating: 802BGA/_Setup.dll       
arion@ubuntu:~$ cd 802BGA
arion@ubuntu:~/802BGA$ sudo ndiswrapper -i netathr.inf
sudo: ndiswrapper: command not found
arion@ubuntu:~/802BGA$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
arion@ubuntu:~/802BGA$ sudo rmmod ath_pci
arion@ubuntu:~/802BGA$ sudo rmmod ath5k
ERROR: Module ath5k does not exist in /proc/modules
arion@ubuntu:~/802BGA$ sudo depmod -a
arion@ubuntu:~/802BGA$ sudo modprobe ndiswrapper
arion@ubuntu:~/802BGA$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
arion@ubuntu:~/802BGA$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
arion@ubuntu:~/802BGA$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

arion@ubuntu:~/802BGA$ dmesg | grep -e ndis -e wlan
[   10.012401] wlan: 0.9.4
[  568.248125] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  568.261063] usbcore: registered new interface driver ndiswrapper
arion@ubuntu:~/802BGA$ pwd
/home/arion/802BGA
arion@ubuntu:~/802BGA$

---

### Post by pytheas22 on 2009-01-02
Sorry for not responding in time to save you from having to hook up to ethernet.

It looks like the package ndiswrapper-common is not being found for you for some reason.  Luckily, however, that package should be on your Ubuntu live CD.  So put your CD in the drive, then go to System>Administration>Software Source.  Under the 'Ubuntu Software' tab, you should see a box to enable use of your CD as a repository.  Check that box and uncheck all the other boxes (since they require an Internet connection), then close the window.  If you're asked to reload the sources list, say yes.

Now type these commands and ndiswrapper should be installed:
```

sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```

Do you still get messages about the package not being found?

---

### Post by arionadouble on 2009-01-02
no this is what i got



arion@ubuntu:~$ sudo apt-get update
[sudo] password for arion: 
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done            
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
arion@ubuntu:~$ sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/55.9kB of archives.
After this operation, 225kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter


i had the cd in and pressed enter but nothing happened twice
the next time i boot up i will have to have the cd in the cd rom won't i and also i am not positive i have the live version i downloaded this directly from the ubuntu website version 8.10 it may be the live version but im not positive

---

### Post by pytheas22 on 2009-01-02
hmmm, that's weird that it can't locate the CD.  I'm sorry that you're having so much trouble.

Does rebooting with the CD in the drive make a difference?

Another way of installing these two packages is to open up the live CD in a file browser (you should be able to find it under the main 'Places' menu) and navigate to pool>main>n>ndiswrapper.  At that location, you should find two packages.  Click each on to install it.  If it complains about unsatisfied dependencies, try installing the other package first (one package needs to be installed before the other one, but I forget which should come first).

Please let me know if either of these suggestions allows you to get ndiswrapper installed.
> 
i am not positive i have the live version i downloaded this directly from the ubuntu website version 8.10 it may be the live version but im not positive

You probably have the live CD.  The only other CD you could have would be the alternate CD, which has an ugly text-based installer and doesn't allow you to 'try' Ubuntu before installing.  The default option on the Ubuntu website is to download the live CD.

---

### Post by arionadouble on 2009-01-02
okay so i got to the two packets i opened the first one an error popped up : wrong architecture 'i 386'. So i did as you said and opened the second and it installed successfully.  Once trying to install the first one again i couldn't the same error popped up.

---

### Post by albinootje on 2009-01-02
> **arionadouble said:**
> okay so i got to the two packets i opened the first one an error popped up : wrong architecture 'i 386'. So i did as you said and opened the second and it installed successfully.  Once trying to install the first one again i couldn't the same error popped up.

Okay, what does :
```

ndiswrapper -l 

```
say now ?

---

### Post by arionadouble on 2009-01-02
it says
ERROR: no ndiswrapper utils found!
dang!!!!

---

### Post by albinootje on 2009-01-02
> **arionadouble said:**
> it says
ERROR: no ndiswrapper utils found!
dang!!!!

Sorry, my reply was too quick, I should have carefully read all of the comments. 
The moment I read that you wrote that the other cdrom worked, I assumed that installing ndiswrapper was successfully after that.

Can you please try the following, type in :

```

sudo apt-cdrom add

```
Put your 8.10 installation cdrom in, and let it scan.
After that, do :
```

sudo apt-get install ndiswrapper ndiswrapper-utils-1.9
wget ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip
unzip WLan*
cd 802BGA
sudo ndiswrapper -i netathr.inf
sudo rmmod ath9k
sudo rmmod ath_pci
sudo rmmod ath5k
sudo depmod -a
sudo modprobe ndiswrapper
ndiswrapper -l
sudo iwlist scan
dmesg | grep -e ndis -e wlan
pwd

```

---

### Post by arionadouble on 2009-01-02
on it 
i believe this is the same process i formely did to no avail. either way im on it 
brb

---

### Post by arionadouble on 2009-01-02
so i did this but it came up to replace some files so i did it for all files let me know if this needs to be changed back because i am not sure otherwise here is what took place

arion@ubuntu:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [626d2e64021194cf85c8bdcaf7f3ddd3-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
E: Unable to locate any package files, perhaps this is not a Debian Disc:confused:
arion@ubuntu:~$ sudo apt-get install ndiswrapper ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper
arion@ubuntu:~$ wget [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan)
--2009-01-02 17:37:34--  [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan)
           => `WLan'
Resolving ftp.work.acer-euro.com... failed: Name or service not known.
wget: unable to resolve host address `ftp.work.acer-euro.com'
arion@ubuntu:~$ wget [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip)
--2009-01-02 17:37:47--  [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip)
           => `WLan Driver 802BGA.zip.1'
Resolving ftp.work.acer-euro.com... failed: Name or service not known.
wget: unable to resolve host address `ftp.work.acer-euro.com'
arion@ubuntu:~$ unzip WLan*
Archive:  WLan Driver 802BGA.zip
replace 802BGA/athr.sys? :([y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: 802BGA/athr.sys         
replace 802BGA/athrext.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: a
error:  invalid response [a]
replace 802BGA/athrext.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
  inflating: 802BGA/athrext.cat      
  inflating: 802BGA/athrextx.cat     
  inflating: 802BGA/athrx.sys        
  inflating: 802BGA/data1.cab        
  inflating: 802BGA/data1.hdr        
  inflating: 802BGA/data2.cab        
  inflating: 802BGA/ISSetup.dll      
  inflating: 802BGA/layout.bin       
  inflating: 802BGA/netathr.inf      
  inflating: 802BGA/netathrx.inf     
  inflating: 802BGA/Notes.txt        
  inflating: 802BGA/setup.exe        
  inflating: 802BGA/setup.ini        
  inflating: 802BGA/setup.inx        
  inflating: 802BGA/setup.iss        
  inflating: 802BGA/_Setup.dll       
arion@ubuntu:~$ cd 802BGA
arion@ubuntu:~/802BGA$ sudo ndiswrapper -i netathr.inf
Error: no ndiswrapper utils found!
arion@ubuntu:~/802BGA$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
arion@ubuntu:~/802BGA$ sudo rmmod ath_pci
arion@ubuntu:~/802BGA$ sudo rmmod ath5k
ERROR: Module ath5k does not exist in /proc/modules
arion@ubuntu:~/802BGA$ sudo depmod -a
arion@ubuntu:~/802BGA$ sudo modprobe ndiswrapper
arion@ubuntu:~/802BGA$ ndiswrapper -l
Error: no ndiswrapper utils found!
arion@ubuntu:~/802BGA$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

arion@ubuntu:~/802BGA$ dmesg | grep -e ndis -e wlan
[   11.544837] wlan: 0.9.4
[  405.583033] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  405.599489] usbcore: registered new interface driver ndiswrapper
arion@ubuntu:~/802BGA$ pwd
/home/arion/802BGA
arion@ubuntu:~/802BGA$

---

### Post by albinootje on 2009-01-02
> **arionadouble said:**
> 
arion@ubuntu:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [626d2e64021194cf85c8bdcaf7f3ddd3-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
E: Unable to locate any package files, perhaps this is not a Debian Disc

Which Ubuntu cdrom (or dvd) did you use to install ?
It should be the desktop installation cdrom, and the one for your architecture (32 or 64 bit).

Can you post the output of :
```

uname -m
cat /etc/apt/sources.list

```
Thanks.

---

### Post by arionadouble on 2009-01-02
desktop installation version 8.10 from the ubuntu site for 32 bit

---

### Post by albinootje on 2009-01-02
> **arionadouble said:**
> desktop installation version 8.10 from the ubuntu site for 32 bit

Hmmm.. In an earlier comment you posted apt-get asked for a 64 bit Ubuntu cdrom.

Can you please post the output of this ?
```

lsb_release -a
uname -m
cat /etc/apt/sources.list

```
Thanks in advance.

---

### Post by arionadouble on 2009-01-02
arion@ubuntu:~$ uname -m
x86_64
arion@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
arion@ubuntu:~$ :confused:

---

### Post by albinootje on 2009-01-02
> **arionadouble said:**
> arion@ubuntu:~$ uname -m
x86_64
arion@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted

You have a 64 bit kernel installed, and you have a 64 bit Ubuntu cdrom in the sources.list.
Then you need the 64 bit Ubuntu installation cdrom, to proceed, I'd say.

This one :
[http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.iso](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.iso)

---

### Post by arionadouble on 2009-01-02
im running a 32 bit os(vista) should i have a 64 bit os (ubuntu)

---

### Post by albinootje on 2009-01-02
> **arionadouble said:**
> im running a 32 bit os(vista) should i have a 64 bit os (ubuntu)

64-bit has only advantages for a desktop user who needs to do heavy calculations, that's what I've read about it.

Do you have your important data backed up, and you want to reinstall with your 32 bit Ubuntu desktop installation cdrom ?
Is that what you're asking ?
Sure, go ahead!

:)

---

### Post by arionadouble on 2009-01-02
that's what im asking.  im running a dual boot though and have partitioned for ubuntu so should i just rid the partition and start fresh afterdownloading the 32 bit linux which is what i thought that i had downloaded.  Do you think that this may fix my problem or just give me the better os for my needs.  im just really trying to get this fixed i want to make the full switch to ubuntu but have to have an internet connection.  since the 64 bit is what i have and it is working besides the fact of no wireless should i just stick with it.

---

### Post by albinootje on 2009-01-02
> **arionadouble said:**
> that's what im asking.  im running a dual boot though and have partitioned for ubuntu so should i just rid the partition and start fresh afterdownloading the 32 bit linux which is what i thought that i had downloaded.  Do you think that this may fix my problem or just give me the better os for my needs.  im just really trying to get this fixed i want to make the full switch to ubuntu but have to have an internet connection.  since the 64 bit is what i have and it is working besides the fact of no wireless should i just stick with it.

According to the output you've posted, you have the 64 bit Ubuntu installed.

My personal opinion is that people, who want a desktop system, and who are new to Ubuntu should stick to the 32 bit version of the Ubuntu installation.
That makes things easier for flash-player and Java installations, and probably some more rather important things.

So, go for the 32 bit Ubuntu.

---

### Post by pytheas22 on 2009-01-02
> okay so i got to the two packets i opened the first one an error popped up : wrong architecture 'i 386'. So i did as you said and opened the second and it installed successfully. Once trying to install the first one again i couldn't the same error popped up.

That's really weird.  That CD that you were using definitely looks like it's 64-bit, so I don't know why it thinks the packages on it are for 32-bit machines.

But anyway, things would be easier if you just installed 32-bit Ubuntu.  64-bit can be a little faster in some respects, but for normal home users there's not a big difference.  You can download the 32-bit ISO [here]("http://www.ubuntu.com/getubuntu/download"); make sure that under the 'Custom Options' section, you check  '32bit version' (this should be the default).

After you get the 32-bit version of Ubuntu installed, please add your CD-ROM as a repository as you did before, then run these commands again to install ndiswrapper:
```

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

After that, we'll need to install Windows drivers into ndiswrapper, but I'll give you instructions for that when the time comes (don't install using the driver that I linked to earlier because it won't work on a 32-bit system).

---

### Post by arionadouble on 2009-01-03
okay just one question before i do this im wanting to have beryl is there a different download specifically for this or once i get ubuntu up and running i can just install beryl

---

### Post by albinootje on 2009-01-03
> **arionadouble said:**
> okay just one question before i do this im wanting to have beryl is there a different download specifically for this or once i get ubuntu up and running i can just install beryl

Beryl's successor is called compiz.
Should be included.
You need 3D accel. for that with your video driver for your videocard.
What video card has your machine ?

---

### Post by arionadouble on 2009-01-03
Nvidia gforce 7500le

---

### Post by albinootje on 2009-01-03
> **arionadouble said:**
> Nvidia gforce 7500le

Good! :)

---

### Post by arionadouble on 2009-01-03
upon downloading the 32 bit os should i extract the files and then burn to a disc or burn to a disc first

---

### Post by albinootje on 2009-01-03
> **arionadouble said:**
> upon downloading the 32 bit os should i extract the files and then burn to a disc or burn to a disc first

You should download the iso file, and then burn it as iso, not as data.

See here :
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by arionadouble on 2009-01-03
all right im doing it now thanks for the patience

---

### Post by arionadouble on 2009-01-03
okay ive downloaded the 32 bit and have burned the iso image to a dvdr and cant seem to get it to boot can u help or do you want me to jump over to a different support category

---

### Post by pytheas22 on 2009-01-03
> okay ive downloaded the 32 bit and have burned the iso image to a dvdr and cant seem to get it to boot can u help or do you want me to jump over to a different support category

What happens when you try to boot to it?  Do you get to the screen with a menu, the first option of which says something like "Try Ubuntu without making any changes to your computer?"

Or do you just get an error from BIOS when you try to boot to the DVD.  If that happens, are you positive that you burnt the ISO file as an image, not as data?  There are detailed instructions [here]("http://www.psychocats.net/ubuntu/iso") of how to burn an ISO properly (they're for Ubuntu 7.10, but should apply to 8.10 just as well).

---

### Post by arionadouble on 2009-01-04
so i got the 32 bit reloaded and did the software sources menu like you told me and then this is what i got 

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

arion@ubuntu:~$ sudo apt-get update
[sudo] password for arion: 
Sorry, try again.
[sudo] password for arion: 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/restricted Translation-en_US
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
arion@ubuntu:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/55.9kB of archives.
After this operation, 225kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press ente

arion@ubuntu:~$ sudo apt-get update
[sudo] password for arion: 
Sorry, try again.
[sudo] password for arion: 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/restricted Translation-en_US
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
arion@ubuntu:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/55.9kB of archives.
After this operation, 225kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press ente

---

### Post by arionadouble on 2009-01-04
once it got here i pressed enter but i saw no change

---

### Post by albinootje on 2009-01-04
> **arionadouble said:**
> so i got the 32 bit reloaded and did the software sources menu like you told me and then this is what i got 
-- cut --
Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter 

According to you, you have installed the 32 bit now, and it still asks for the 64 bit cdrom ?
And when you put the installation cdrom in the disk it still gives these errors ?
Can you please post the output of /etc/apt/sources.list here ?
Thanks.

---

### Post by pytheas22 on 2009-01-04
> According to you, you have installed the 32 bit now, and it still asks for the 64 bit cdrom ?
And when you put the installation cdrom in the disk it still gives these errors ?
Can you please post the output of /etc/apt/sources.list here ?
Thanks.

Yes, please post the output of:
```

cat /etc/apt/sources.list
uname -rm
```

---

### Post by arionadouble on 2009-01-04
i am assuming from this read out that i reloaded the 32 bit and if so i have know idea how to download the 32 bit because i got this directly from the ubuntu website with 32 bit version chose. neway here you go

/etc/apt/sources.list arion@ubuntu:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
arion@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
arion@ubuntu:~$ uname -rm
2.6.27-7-generic x86_64


cat /etc/apt/sources.list
uname -rm

arion@ubuntu:~$ arion@ubuntu:~$ /etc/apt/sources.list
bash: arion@ubuntu:~$: command not found
arion@ubuntu:~$ bash: /etc/apt/sources.list: Permission denied
bash: bash:: command not found
arion@ubuntu:~$ arion@ubuntu:~$ cat /etc/apt/sources.list
bash: arion@ubuntu:~$: command not found
arion@ubuntu:~$ deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
bash: syntax error near unexpected token `('
arion@ubuntu:~$ # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
arion@ubuntu:~$ # newer versions of the distribution.
arion@ubuntu:~$ 
arion@ubuntu:~$ 
arion@ubuntu:~$ ## Major bug fix updates produced after the final release of thearion@ubuntu:~$ ## distribution.
arion@ubuntu:~$ deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
bash: deb: command not found
arion@ubuntu:~$ 
arion@ubuntu:~$ ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
arion@ubuntu:~$ ## team. Also, please note that software in universe WILL NOT receive any
arion@ubuntu:~$ ## review or updates from the Ubuntu security team.
arion@ubuntu:~$ 
arion@ubuntu:~$ ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
arion@ubuntu:~$ ## team, and may not be under a free licence. Please satisfy yourself as to 
arion@ubuntu:~$ ## your rights to use the software. Also, please note that software in 
arion@ubuntu:~$ ## multiverse WILL NOT receive any review or updates from the Ubuntu
arion@ubuntu:~$ ## security team.
arion@ubuntu:~$ 
arion@ubuntu:~$ ## Uncomment the following two lines to add software from the 'backports'
arion@ubuntu:~$ ## repository.
arion@ubuntu:~$ ## N.B. software from this repository may not have been tested as
arion@ubuntu:~$ ## extensively as that contained in the main release, although it includes
arion@ubuntu:~$ ## newer versions of some applications which may provide useful features.
arion@ubuntu:~$ ## Also, please note that software in backports WILL NOT receive any review
arion@ubuntu:~$ ## or updates from the Ubuntu security team.
arion@ubuntu:~$ # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
arion@ubuntu:~$ # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
arion@ubuntu:~$ 
arion@ubuntu:~$ ## Uncomment the following two lines to add software from Canonical's
arion@ubuntu:~$ ## 'partner' repository. This software is not part of Ubuntu, but is
arion@ubuntu:~$ ## offered by Canonical and the respective vendors as a service to Ubuntu
arion@ubuntu:~$ ## users.
arion@ubuntu:~$ # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
arion@ubuntu:~$ # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
arion@ubuntu:~$ 
arion@ubuntu:~$ # Line commented out by installer because it failed to verify:
arion@ubuntu:~$ # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
arion@ubuntu:~$ # Line commented out by installer because it failed to verify:
arion@ubuntu:~$ # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
arion@ubuntu:~$ # Line commented out by installer because it failed to verify:
arion@ubuntu:~$ # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
arion@ubuntu:~$ # Line commented out by installer because it failed to verify:
arion@ubuntu:~$ # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
arion@ubuntu:~$ # Line commented out by installer because it failed to verify:
arion@ubuntu:~$ # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
arion@ubuntu:~$ # Line commented out by installer because it failed to verify:
arion@ubuntu:~$ # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
arion@ubuntu:~$ arion@ubuntu:~$ uname -rm
bash: arion@ubuntu:~$: command not found
arion@ubuntu:~$ 2.6.27-7-generic x86_64
bash: 2.6.27-7-generic: command not found
arion@ubuntu:~$ arion@ubuntu:~$ 
bash: arion@ubuntu:~$: command not found
arion@ubuntu:~$

---

### Post by albinootje on 2009-01-04
> **arionadouble said:**
> 
arion@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
-- cut --
arion@ubuntu:~$ arion@ubuntu:~$ uname -rm
bash: arion@ubuntu:~$: command not found
arion@ubuntu:~$ 2.6.27-7-generic x86_64

OK, you have the 64 bit Ubuntu installed again, which is OK, but I don't understand why the installation of Ndiswrapper from cdrom seems to fail.

Do you have a problem with the copy and pasting somehow ?
Can you post the output of the following :
```

dpkg -l|grep -i ndis

```

---

### Post by arionadouble on 2009-01-04
when i do that command it just drops down to the next command line nothing happened

---

### Post by albinootje on 2009-01-04
> **arionadouble said:**
> when i do that command it just drops down to the next command line nothing happened

That's fine. 
It means that ndiswrapper was not installed.

Can you try this now :
```

sudo apt-get install smbclient

```
This is a small program which you might not need, but should be on the cdrom for sure!
Please post the output, thanks.

---

### Post by arionadouble on 2009-01-04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbclient is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

okay so i have a quick question when i was told to use the cd as a repository(i think thats right) i was told to check that box and uncheck the rest.  well when i checked that box and then unchecked the rest the source code box which was unchecked to begin with checked it self.  since i was told to uncheck the rest of the boxes i unchecked it as i thought that i should.  may not have anything to do with this but i just wanted to be sure.  so what are we thinkn now

---

### Post by albinootje on 2009-01-04
> **arionadouble said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbclient is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Ooops... smbclient is already installed by default..
Can you try this :
```

sudo apt-get install nmap

```

> 
okay so i have a quick question when i was told to use the cd as a repository(i think thats right) i was told to check that box and uncheck the rest.
It's fine to only use the cdrom for now since you have no internet on that machine yet.

---

### Post by arionadouble on 2009-01-04
sudo apt-get install nmap

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nmap

---

### Post by albinootje on 2009-01-04
> **arionadouble said:**
>  E: Couldn't find package nmap

Hmmm :(

Can you do this :
```

sudo apt-get install build-essential

```

And meanwhile download these on another machine onto an usb stick :
[http://packages.ubuntu.com/intrepid/all/ndiswrapper-common/download](http://packages.ubuntu.com/intrepid/all/ndiswrapper-common/download)
[http://packages.ubuntu.com/intrepid/amd64/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/intrepid/amd64/ndiswrapper-utils-1.9/download)

---

### Post by arionadouble on 2009-01-04
sudo apt-get install build-essential

arion@ubuntu:~$ sudo apt-get install build-essential
[sudo] password for arion: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6932kB of archives.
After this operation, 23.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter


i pressed enter twice and it started working then abruptly stopped 

i downloaded the links you provided

---

### Post by albinootje on 2009-01-05
> **arionadouble said:**
>  i downloaded the links you provided

Can you copy those two files to your Ubuntu disk to the /tmp directory.
Then open a terminal, and type in :
```

sudo dpkg -i /tmp/ndis*deb

```
Please post any errors.

By the way, if you find the chance to get online somewhere with your machine with a wired connection, that would make things so much easier.
Let us know :)

---

### Post by arionadouble on 2009-01-05
i can connect via wired connection should i do that first and then do these commands

---

### Post by albinootje on 2009-01-05
> **arionadouble said:**
> i can connect via wired connection should i do that first and then do these commands

Excellent.
Once you have the wired connection, then enable the repositories again like they were before (main,security,univers,multiverse), and then follow the long Ndiswrapper installation instructions which was posted by someone else earlier in this thread.

---

### Post by albinootje on 2009-01-05
The instructions from the ones from comment #17.

---

### Post by arionadouble on 2009-01-05
im doing in now and it seems to be working it  is currently downloading something and i will post the output when im done

---

### Post by arionadouble on 2009-01-05
this is what i got

arion@ubuntu:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
[sudo] password for arion: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 210 not upgraded.
Need to get 55.9kB of archives.
After this operation, 225kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main ndiswrapper-common 1.52-1ubuntu1 [20.2kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main ndiswrapper-utils-1.9 1.52-1ubuntu1 [35.7kB]
Fetched 55.9kB in 0s (56.5kB/s)             
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 99179 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.52-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.52-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.52-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.52-1ubuntu1) ...
arion@ubuntu:~$ wget [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip)
--2009-01-05 16:57:02--  [ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip](ftp://ftp.work.acer-euro.com/notebook/ferrari_5000/vista/Drivers/WLan%20Driver%20802BGA.zip)
           => `WLan Driver 802BGA.zip'
Resolving ftp.work.acer-euro.com... 193.0.238.152
Connecting to ftp.work.acer-euro.com|193.0.238.152|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /notebook/ferrari_5000/vista/Drivers ... done.
==> SIZE WLan Driver 802BGA.zip ... 2689538
==> PASV ... done.    ==> RETR WLan Driver 802BGA.zip ... done.
Length: 2689538 (2.6M)

100%[======================================>] 2,689,538   --.-K/s   in 4m 3s   

2009-01-05 17:01:10 (10.8 KB/s) - `WLan Driver 802BGA.zip' saved [2689538]

arion@ubuntu:~$ unzip WLan*
Archive:  WLan Driver 802BGA.zip
   creating: 802BGA/
  inflating: 802BGA/athr.sys         
  inflating: 802BGA/athrext.cat      
  inflating: 802BGA/athrextx.cat     
  inflating: 802BGA/athrx.sys        
  inflating: 802BGA/data1.cab        
  inflating: 802BGA/data1.hdr        
  inflating: 802BGA/data2.cab        
  inflating: 802BGA/ISSetup.dll      
  inflating: 802BGA/layout.bin       
  inflating: 802BGA/netathr.inf      
  inflating: 802BGA/netathrx.inf     
  inflating: 802BGA/Notes.txt        
  inflating: 802BGA/setup.exe        
  inflating: 802BGA/setup.ini        
  inflating: 802BGA/setup.inx        
  inflating: 802BGA/setup.iss        
  inflating: 802BGA/_Setup.dll       
arion@ubuntu:~$ cd 802BGA
arion@ubuntu:~/802BGA$ sudo ndiswrapper -i netathr.inf
installing netathr ...
couldn't find models section "Atheros" -
installation may be incomplete
arion@ubuntu:~/802BGA$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
arion@ubuntu:~/802BGA$ sudo rmmod ath_pci
arion@ubuntu:~/802BGA$ sudo rmmod ath5k
ERROR: Module ath5k does not exist in /proc/modules
arion@ubuntu:~/802BGA$ sudo depmod -a
arion@ubuntu:~/802BGA$ sudo modprobe ndiswrapper
arion@ubuntu:~/802BGA$ ndiswrapper -l
netathr : invalid driver!
arion@ubuntu:~/802BGA$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

arion@ubuntu:~/802BGA$ dmesg | grep -e ndis -e wlan
[   12.282646] wlan: 0.9.4
[  925.795922] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  925.818927] usbcore: registered new interface driver ndiswrapper
arion@ubuntu:~/802BGA$ pwd
/home/arion/802BGA
arion@ubuntu:~/802BGA$

---

### Post by albinootje on 2009-01-05
> **arionadouble said:**
> 
arion@ubuntu:~/802BGA$ sudo ndiswrapper -i netathr.inf
installing netathr ...
couldn't find models section "Atheros" -
installation may be incomplete
-- cut --
arion@ubuntu:~/802BGA$ ndiswrapper -l
netathr : invalid driver!

We're making good progress! :)
Except that you probably need another Windows driver to load with Ndiswrapper.

---

### Post by arionadouble on 2009-01-05
so what then should i do try to find the driver

---

### Post by albinootje on 2009-01-05
> **arionadouble said:**
> so what then should i do try to find the driver

I just looked at those drivers, please try with the other .inf file (which is for 64 bit) as following :

```

cd ~/802BGA
sudo ndiswrapper -i netathrx.inf
sudo ndiswrapper -l

```

---

### Post by arionadouble on 2009-01-05
arion@ubuntu:~/802BGA$ sudo ndiswrapper -i netathrx.inf
[sudo] password for arion: 
installing netathrx ...
arion@ubuntu:~/802BGA$ sudo ndiswrapper -l
netathr : invalid driver!
netathrx : driver installed
	device (168C:001B) present (alternate driver: ath_pci)
arion@ubuntu:~/802BGA$

---

### Post by albinootje on 2009-01-05
> **arionadouble said:**
> arion@ubuntu:~/802BGA$ sudo ndiswrapper -i netathrx.inf
[sudo] password for arion: 
installing netathrx ...
arion@ubuntu:~/802BGA$ sudo ndiswrapper -l
netathr : invalid driver!
netathrx : driver installed
	device (168C:001B) present (alternate driver: ath_pci)
arion@ubuntu:~/802BGA$

OK, good! And now :
```

sudo ndiswrapper -e netathr
sudo modprobe -r ath_pci ath_hal
sudo ifconfig -a
sudo iwconfig
sudo iwlist scan

```

---

### Post by arionadouble on 2009-01-05
arion@ubuntu:~/802BGA$ sudo ndiswrapper -e netathr
arion@ubuntu:~/802BGA$ sudo modprobe -r ath_pci ath_hal
arion@ubuntu:~/802BGA$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:60:c1:35:2f  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fec1:352f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18978210 (18.9 MB)  TX bytes:1226947 (1.2 MB)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

pan0      Link encap:Ethernet  HWaddr b2:15:d1:fd:82:97  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

arion@ubuntu:~/802BGA$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

arion@ubuntu:~/802BGA$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

arion@ubuntu:~/802BGA$ 

was i supposed to open a new terminal first since it still read 
arion@ubuntu:~/802BGA$

---

### Post by albinootje on 2009-01-05
OK. can you do the following from here :
[http://ubuntuforums.org/archive/index.php/t-503769.html](http://ubuntuforums.org/archive/index.php/t-503769.html)
> 
gksu gedit /etc/modprobe.d/blacklist

Add to the bottom of the file:
blacklist ath_pci
blacklist ath_hal

Then :
> 
gksu gedit /etc/modules
Add to the bottom of the file :
ndiswrapper

Reboot.

After reboot, try :
```

sudo ndiswrapper -l
sudo iwconfig
sudo iwlist scan

```

---

### Post by arionadouble on 2009-01-05
so should i start this with a new terminal or go from cd802BGA

---

### Post by albinootje on 2009-01-05
> **arionadouble said:**
> so should i start this with a new terminal or go from cd802BGA

After the reboot this should not matter anymore, because ndiswrapper did claim that the 64 bit Windows driver was taken in use.

---

### Post by arionadouble on 2009-01-05
arion@ubuntu:~$ sudo ndiswrapper -l
[sudo] password for arion: 
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with 'ndiswrapper'
netathrx : driver installed
	device (168C:001B) present (alternate driver: ath_pci)
arion@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

arion@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

arion@ubuntu:~$

---

### Post by albinootje on 2009-01-05
> **arionadouble said:**
> arion@ubuntu:~$ sudo ndiswrapper -l
[sudo] password for arion: 
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with 'ndiswrapper'
netathrx : driver installed
	device (168C:001B) present (alternate driver: ath_pci)

You made a little mistake. 
Can you correct the ndiswrapper line in /etc/modprobe.d/blacklist ?

It should be like this :
```

# Begin example bottom line of /etc/modprobe.d/blacklist :
blacklist ath_pci
blacklist ath_hal
# End example bottom line of /etc/modprobe.d/blacklist

```
And :

```

# Begin example bottom line of /etc/modules :
ndiswrapper
# Begin example bottom line of /etc/modules

```
After that reboot again, and please post the output of :
```

lsmod|grep ath
ndiswrapper -l

```

---

### Post by arionadouble on 2009-01-05
okay some im not smart i forgot where it was saved and cant find it can u give me a hint

---

### Post by arionadouble on 2009-01-05
also im not exactly understanding what you need me to do.  am i editing the file again or doing this in the terminal

---

### Post by albinootje on 2009-01-05
> **arionadouble said:**
> also im not exactly understanding what you need me to do.  am i editing the file again or doing this in the terminal

You need to do this :

```

 gksu gedit /etc/modprobe.d/blacklist

```

Add to the bottom of the file:
blacklist ath_pci
blacklist ath_hal

Then :
```

gksu gedit /etc/modules

```
Add to the bottom of the file :
ndiswrapper

You got a syntax error about ndiswrapper in /etc/modprobe.d/blacklist around line 48, but ndiswrapper should be added in /etc/modules instead.
So.. can you remove the ndiswrapper word from /etc/modprobe.d/blacklist at the bottom ?
And follow the instructions mentioned above.

---

### Post by arionadouble on 2009-01-05
arion@ubuntu:~$ gksu gedit /etc/modprobe.d/blacklist
gksu gedit /etc/modules

this is what i have in the terminal in the order that was stated

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
blacklist ath_pci
blacklist ath_hal
ndiswrapper

this is what i have in the file after redoing what you told me
now should i save the file

---

### Post by albinootje on 2009-01-06
> **arionadouble said:**
> arion@ubuntu:~$ gksu gedit /etc/modprobe.d/blacklist
-- cut --

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
blacklist ath_pci
blacklist ath_hal
ndiswrapper


You should remove the ndiswrapper line here from that file.
Save the file, and then open another file :
```

gksu gedit /etc/modules

```
then add the word ndiswrapper in a new line at the bottom of that file /etc/modules and save it.

Please also install ndisgtk :
```

apt-get install ndisgtk

```
Thanks.

---

### Post by arionadouble on 2009-01-07
arion@ubuntu:~$ apt-get install ndisgtk
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
arion@ubuntu:~$ sudo apt-get install ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 77.1kB of archives.
After this operation, 676kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main ndiswrapper-common 1.52-1ubuntu1 [20.2kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main ndiswrapper-utils-1.9 1.52-1ubuntu1 [35.1kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main ndisgtk 0.8.4-1 [21.7kB]
Fetched 77.1kB in 1s (66.1kB/s)
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 127508 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.52-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb) ...
Selecting previously deselected package ndisgtk.
Unpacking ndisgtk (from .../ndisgtk_0.8.4-1_i386.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.52-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.52-1ubuntu1) ...
Setting up ndisgtk (0.8.4-1) ...

okay should i check the wireless connection

---

### Post by albinootje on 2009-01-07
> **arionadouble said:**
> 
Setting up ndisgtk (0.8.4-1) ...

okay should i check the wireless connection

Good.

Go here : -> System -> Administration -> Windows Wireless Drivers

The ndisgtk package is meant to make installing and removing Windows wifi drivers easier.

---

