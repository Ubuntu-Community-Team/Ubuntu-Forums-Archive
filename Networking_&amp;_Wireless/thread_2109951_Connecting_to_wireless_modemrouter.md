---
title: "Connecting to wireless modem/router"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by stevesy on 2013-01-28
Hi guys I'm new to Ubuntu forums and to Linux, recently installed Lubuntu 12.10 on my Dell netbook via wubi.  I haven't been able to connect to my wireless modem/router (Cisco epc2425).  Tried creating a wireless connection in "network connections" and configuring it but no joy so far.  There doesn't seem to be a way of scanning for/showing wireless networks in range, so I'm guessing I need to install something for that or use a command of some kind?  Help appreciated, thanks.

---

### Post by ACubed10 on 2013-01-28
what wireless card is in your laptop?  Sounds like you will need to install a driver for it!

---

### Post by stevesy on 2013-01-29
> **ACubed10 said:**
> what wireless card is in your laptop?  Sounds like you will need to install a driver for it!

Hi ACubed10 it's a Dell Wireless 1395 WLAN Mini-Card.

---

### Post by Bucky Ball on 2013-01-29
*Thread moved to **Networking & Wireless ***

---

### Post by stevesy on 2013-01-29
In case it's of any help..


steve@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GSE Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
02:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
02:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
steve@ubuntu:~$ lsmod
Module                  Size  Used by
rfcomm                 37277  0 
bnep                   17708  2 
bluetooth             183270  10 rfcomm,bnep
parport_pc             31969  0 
ppdev                  12818  0 
snd_hda_codec_realtek    63496  1 
snd_hda_intel          32516  1 
snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
joydev                 17162  0 
coretemp               13169  0 
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
hid_generic            12485  0 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
b43                   347311  0 
mac80211              461203  1 b43
snd                    62146  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  457247  2 
uvcvideo               71278  0 
dell_laptop            17162  0 
drm_kms_helper         47304  1 i915
videobuf2_core         32071  1 uvcvideo
drm                   238811  3 i915,drm_kms_helper
cfg80211              175574  2 b43,mac80211
compal_laptop          19251  0 
videodev               95842  2 uvcvideo,videobuf2_core
ses                    17172  0 
videobuf2_vmalloc      12757  1 uvcvideo
soundcore              14600  1 snd
jmb38x_ms              17178  0 
lp                     13300  0 
dcdbas                 14055  1 dell_laptop
microcode              18210  0 
psmouse                84878  0 
enclosure              14692  1 ses
serio_raw              13032  0 
videobuf2_memops       13213  1 videobuf2_vmalloc
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
lpc_ich                16926  0 
memstick               15843  1 jmb38x_ms
bcma                   34484  1 b43
i2c_algo_bit           13198  1 i915
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
mac_hid                13038  0 
video                  18848  1 i915
parport                40754  3 parport_pc,ppdev,lp
uas                    17557  0 
usb_storage            39351  1 
nls_iso8859_1          12618  1 
ssb                    50088  1 b43
r8169                  55977  0 
sdhci_pci              18156  0 
sdhci                  27831  1 sdhci_pci
steve@ubuntu:~$ rfkill list all
0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
steve@ubuntu:~$ sudo lshw -c network
[sudo] password for steve: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:ee:de:84
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0610000-f0610fff memory:f0600000-f060ffff memory:f0620000-f063ffff
steve@ubuntu:~$

---

### Post by stevesy on 2013-01-30
My wireless connection is working now!  I used 

sudo apt-get install linux-headers-generic bcmwl-kernel-source
sudo modprobe wl

which I found at  [http://ubuntuforums.org/showthread.php?t=2092871](http://ubuntuforums.org/showthread.php?t=2092871)

There were a few error messages in the output and a warning at the end plus, nothing happened when i entered the modprobe wl command.   Hoping this isn't serious, if any of you have the time maybe you could check it out for me, thanks.
  
Output:
  
steve@ubuntu:~$ sudo apt-get install linux-headers-generic bcmwl-kernel-source
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following package was automatically installed and is no longer required:
  libreadline5
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  binutils dkms fakeroot gcc gcc-4.7 libc-dev-bin libc6-dev libgomp1 libitm1
  libquadmath0 linux-libc-dev make manpages-dev
Suggested packages:
  binutils-doc dpkg-dev debhelper gcc-multilib autoconf automake1.9 libtool
  flex bison gdb gcc-doc gcc-4.7-multilib libmudflap0-4.7-dev gcc-4.7-doc
  gcc-4.7-locales libgcc1-dbg libgomp1-dbg libitm1-dbg libquadmath0-dbg
  libmudflap0-dbg binutils-gold glibc-doc make-doc
The following NEW packages will be installed:
  bcmwl-kernel-source binutils dkms fakeroot gcc gcc-4.7 libc-dev-bin
  libc6-dev libgomp1 libitm1 libquadmath0 linux-libc-dev make manpages-dev
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.4 MB of archives.
After this operation, 55.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main libgomp1 i386 4.7.2-2ubuntu1 [29.7 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main libitm1 i386 4.7.2-2ubuntu1 [35.5 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main libquadmath0 i386 4.7.2-2ubuntu1 [198 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main binutils i386 2.22.90.20120924-0ubuntu2 [2,437 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main gcc-4.7 i386 4.7.2-2ubuntu1 [8,506 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main gcc i386 4:4.7.2-1ubuntu2 [5,134 B]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main make i386 3.81-8.2ubuntu2 [116 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main dkms all 2.2.0.3-1.1ubuntu1.1 [71.4 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-libc-dev i386 3.5.0-22.34 [893 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main libc-dev-bin i386 2.15-0ubuntu20 [77.7 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main libc6-dev i386 2.15-0ubuntu20 [5,103 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/restricted bcmwl-kernel-source i386 5.100.82.112+bdcom-0ubuntu3 [1,150 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main fakeroot i386 1.18.4-2 [88.0 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main manpages-dev all 3.40-0.1ubuntu3 [1,710 kB]
Fetched 20.4 MB in 32s (621 kB/s)                                              
Selecting previously unselected package libgomp1:i386.
(Reading database ... 128164 files and directories currently installed.)
Unpacking libgomp1:i386 (from .../libgomp1_4.7.2-2ubuntu1_i386.deb) ...
Selecting previously unselected package libitm1:i386.
Unpacking libitm1:i386 (from .../libitm1_4.7.2-2ubuntu1_i386.deb) ...
Selecting previously unselected package libquadmath0:i386.
Unpacking libquadmath0:i386 (from .../libquadmath0_4.7.2-2ubuntu1_i386.deb) ...
Selecting previously unselected package binutils.
Unpacking binutils (from .../binutils_2.22.90.20120924-0ubuntu2_i386.deb) ...
Selecting previously unselected package gcc-4.7.
Unpacking gcc-4.7 (from .../gcc-4.7_4.7.2-2ubuntu1_i386.deb) ...
Selecting previously unselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.7.2-1ubuntu2_i386.deb) ...
Selecting previously unselected package make.
Unpacking make (from .../make_3.81-8.2ubuntu2_i386.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu1.1_all.deb) ...
Selecting previously unselected package linux-libc-dev:i386.
Unpacking linux-libc-dev:i386 (from .../linux-libc-dev_3.5.0-22.34_i386.deb) ...
Selecting previously unselected package libc-dev-bin.
Unpacking libc-dev-bin (from .../libc-dev-bin_2.15-0ubuntu20_i386.deb) ...
Selecting previously unselected package libc6-dev:i386.
Unpacking libc6-dev:i386 (from .../libc6-dev_2.15-0ubuntu20_i386.deb) ...
Selecting previously unselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_i386.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2_i386.deb) ...
Selecting previously unselected package manpages-dev.
Unpacking manpages-dev (from .../manpages-dev_3.40-0.1ubuntu3_all.deb) ...
Processing triggers for man-db ...
Setting up libgomp1:i386 (4.7.2-2ubuntu1) ...
Setting up libitm1:i386 (4.7.2-2ubuntu1) ...
Setting up libquadmath0:i386 (4.7.2-2ubuntu1) ...
Setting up binutils (2.22.90.20120924-0ubuntu2) ...
Setting up gcc-4.7 (4.7.2-2ubuntu1) ...
Setting up gcc (4:4.7.2-1ubuntu2) ...
Setting up make (3.81-8.2ubuntu2) ...
Setting up dkms (2.2.0.3-1.1ubuntu1.1) ...
Setting up linux-libc-dev:i386 (3.5.0-22.34) ...
Setting up libc-dev-bin (2.15-0ubuntu20) ...
Setting up libc6-dev:i386 (2.15-0ubuntu20) ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-22-generic
Building for architecture i686
Building initial module for 3.5.0-22-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-22-generic/updates/dkms/

depmod.....

DKMS: install completed.
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
update-initramfs: deferring update (trigger activated)
Setting up fakeroot (1.18.4-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up manpages-dev (3.40-0.1ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-22-generic
Warning: No support for locale: en_US.utf8
steve@ubuntu:~$ sudo modprobe wl

---

