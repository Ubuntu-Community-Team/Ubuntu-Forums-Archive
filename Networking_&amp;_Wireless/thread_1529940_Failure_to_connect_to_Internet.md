---
title: "Failure to connect to Internet"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by idku on 2010-07-12
Hi all, first off, i'm totally new. Quick to catch on, but ignorant for the moment. Here's the deal : 

I got a netbook, used, and I installed Ubuntu Netbook Remix on it. This is my netbook : 

> Product Number    VA715UA#ABA
Microprocessor    1.60GHz Intel Atom Processor N270
Microprocessor Cache    512KB L2
Memory    1024MB DDR2 System Memory (1 Dimm)
Memory Max    1024MB
Video Graphics    Intel Graphics Media Accelerator 950
Video Memory    Up to 128MB
Hard Drive    160GB (5400RPM)
Display    10.1” Diagonal SD LED Anti-glare Widescreen Display (1024 x 576)
Network Card    Integrated 10/100 Ethernet LAN
Wireless Connectivity    

    * 802.11b/g WLAN

Sound    

    * HD Audio
    * stereo speakers
    * integrated microphone

Keyboard    82 key (92% Full size)
Pointing Device    Touch Pad with dedicated vertical Scroll Up/Down (note: no on/off button)
External Ports    

    * 5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards
    * 3 Universal Serial Bus (USB) 2.0
    * Headphone-out/Microphone in combo jack (compatible with 3.5mm 4-conductor jack with stereo audio and mono mic)
    * 1 VGA (15-pin)
    * 1 RJ -45 (LAN)

Other Devices    

    * HP Webcam with integrated microphone

Dimensions    10.3 in (L) x 6.77 in (D) x 1.04-1.29 in (H)
Weight    2.57 lbs
Security    

    * Kensington MicroSaver lock slot
    * Power-on password
    * Accepts 3rd party security lock devices

Power    

    * 30W AC Adapter
    * 3-Cell Lithium-Ion battery...yay for me, right? WRONG.

I was fine to get on the internet when it had Vista on it, but now the wifi light is always 'on' no matter what I do, yet Ubuntu can't even acknowledge it HAS wifi, let alone connects. I'm at a total loss here, and I _need_ this up and running. It's seriously urgent. So i'm 100% willing to try any suggestion, or accept any help (with grace) that anybody would give. 

I've found a lot of people with similar issues,  but none of those solutions has helped. My Ubuntu 'fails' packages all the time (tells me they don't exist!) and I don't know what to do with it. I'm a Windows user (born and raised) and speaking Ubuntu is not coming naturally to me... please help...

---

### Post by pytheas22 on 2010-07-12
Please open a terminal from the Applications>Accessories menu, run the following commands and post the output here:
```

lshw -C Network
lspci -nn
uname -rm
dmesg | grep -ie wlan -ie radio
```

Since you can't connect to the Internet with the netbook currently, you can copy and paste the terminal output into a text file, then use a USB drive to transfer it to a different computer so you can post it here easily.

This information will hopefully help us figure out what you need to do to get the wireless working.

---

### Post by idku on 2010-07-12
Give me 5 minutes to do all of that, and i'll post. (Thanks!)

---

### Post by idku on 2010-07-12
lshw -C Network 

> WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:25:b3:61:3d:30
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A ip=192.168.2.9 latency=0 multicast=yes
       resources: irq:26 memory:febc0000-febfffff ioport:ec80(size=128)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:5e:17:5a:b4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

lspci -nn 
> 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
02:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)

---

### Post by idku on 2010-07-12
uname -rm

> 2.6.32-21-generic i686

dmesg | grep -ie wlan -ie radio

> [    6.818384] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    6.993248] Registered led device: b43-phy0::radio

---

### Post by pytheas22 on 2010-07-13
Your card probably just needs firmware installed to work.  Ubuntu doesn't ship firmware for your particular device due to legal issues (the firmware is technically proprietary and the owner won't grant Ubuntu the right to redistribute it), but you can download and install the firmware with a few commands.  While plugged in with ethernet, type:

```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

After the second command, you'll be asked whether you want to install firmware automatically.  Say yes.  Then reboot, and your wireless should hopefully work.  If it still doesn't, please post the output of:
```

dmesg | grep -e b43 -e wlan -ie firmware
ls /lib/firmware
sudo iwlist scan

```

---

### Post by idku on 2010-07-13
You are my Ubuntu hero. I did that, pulled the ethernet cord from the netbook... and it actually showed me my home network. Kudos to you and thank you so much for the help. :D:D:D:D:KS

---

### Post by idku on 2010-07-13
No sooner did I type that... and it kicked me off my home network. I think it hates me. This netbook has evolved it's intelligence, and it's out to get me. lol

---

### Post by pytheas22 on 2010-07-13
Are you still losing the connection to your network?  Did you try rebooting?  If it's a persistent problem, please post the output of these commands after a dropped connection:
```

dmesg | tail -25
dmesg | grep -e wlan -e b43
```

---

### Post by idku on 2010-07-13
A LOT of lines about 'MAC suspend failed'... I can paste them if you want, but there are really a LOT of lines... all saying that with some numbers on the left.

---

### Post by pytheas22 on 2010-07-13
That's strange.  If all of the lines are the same except for the number on the left (which is just a timestamp), you don't have to post all of them, but it would be helpful to see a few examples.

---

### Post by idku on 2010-07-13
Well I did a lot of small bits here and there last night, and new things happened when I entered in your commands today. Also a few changes : 

[INDENT]1. I WAS on my wireless for a few minutes. Then, my green bar (on the WCID icon that a friend helped me install) turned into a blue triangle, and it demanded my key over and over and over... I haven't been on wireless since.
[/INDENT]
[INDENT]2. This DOES work on a hardline... but it's a netbook, sitting in front of my desktop to use it isn't what I had in mind when I bought it.
[/INDENT]
Just wanted to update you... and here are the new results of those two commands you asked me to enter.

dmesg | tail -25

> [   24.900358] __ratelimit: 6 callbacks suppressed
[   24.900369] type=1503 audit(1279032504.711:14):  operation="open" pid=1256 parent=1155 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[   28.758217] atl1c 0000:02:00.0: irq 26 for MSI/MSI-X
[   28.758310] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   33.528045] eth0: no IPv6 routers present
[   76.200279] usb 1-1: new high speed USB device using ehci_hcd and address 3
[   76.336226] usb 1-1: configuration #1 chosen from 1 choice
[   76.423727] Initializing USB Mass Storage driver...
[   76.425121] scsi2 : SCSI emulation for USB Mass Storage devices
[   76.426429] usbcore: registered new interface driver usb-storage
[   76.426452] USB Mass Storage support registered.
[   76.431972] usb-storage: device found at 3
[   76.431980] usb-storage: waiting for device to settle before scanning
[   81.429664] usb-storage: device scan complete
[   81.776442] scsi 2:0:0:0: Direct-Access     Lexar    USB Flash Drive  1100 PQ: 0 ANSI: 0 CCS
[   81.782283] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   81.792316] sd 2:0:0:0: [sdb] 7831552 512-byte logical blocks: (4.00 GB/3.73 GiB)
[   81.793273] sd 2:0:0:0: [sdb] Write Protect is off
[   81.793282] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   81.793288] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   81.798345] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   81.798368]  sdb: sdb1
[   81.803123] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   81.803141] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  140.076408] usb 1-1: USB disconnect, address 3

dmesg | grep -e wlan -e b43

> Nothing happens, simply a new, blank prompt line.

---

### Post by pytheas22 on 2010-07-13
This looks a bit strange.  dmesg (a command that prints out information from your system log) doesn't mention b43 (the wireless driver for your device, which has a Broadcom 43xx chipset) at all.  So it would appear the module is no longer being loaded.  Does the wireless come on if you type:
```

sudo modprobe b43
```

If b43 continues to be problematic--either because it won't load at all, or because the connection drops when loading it--we can try switching to ndiswrapper instead, which would drive your wireless card using Windows drivers.  b43 would be preferable, since it's a native Linux driver with many more features, but sometimes ndiswrapper works better.

---

### Post by bkratz on 2010-07-13
There also is one more option since it uses the BCM4312, that being the sta driver (proprietary version). This link shows a pretty easy installation of same.

[http://ubuntuforums.org/showpost.php?p=9134672&postcount=6](http://ubuntuforums.org/showpost.php?p=9134672&postcount=6)

The link is still active and I have seen a lot of people having good results.

---

### Post by pytheas22 on 2010-07-13
Great point, bkratz.  I didn't think to check whether wl supports this device too but modinfo says it does.  So idfku, if you can't get b43 to work, I'd give the STA driver (a.k.a. 'wl') a try, using the link pointed to above, before going down the ndiswrapper route.

---

### Post by idku on 2010-07-13
> **pytheas22 said:**
> Does the wireless come on if you type:
```

sudo modprobe b43
```

No it doesn't.  :(

Going to try the other suggestion now, will post back soon with the results of that excursion.

---

### Post by idku on 2010-07-13
The results of bkratz's suggestion : 

> Broadcom STA Driver offline installer
for Ubuntu 9.10

by the VigGLUG


Are you sure you want to install this?
Press ENTER to continue

Please do not interrupt the installer...
dpkg: warning: downgrading bcmwl-kernel-source from  5.60.48.36+bdcom-0ubuntu3 to 5.10.91.9+bdcom-0ubuntu4.
(Reading database ... 145123 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3  (using .../bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
dpkg: warning: downgrading dkms from 2.1.1.2-2fakesync1 to  2.1.0.1-0ubuntu1.
Preparing to replace dkms 2.1.1.2-2fakesync1 (using  .../dkms_2.1.0.1-0ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.4ubuntu2_all.deb) ...
dpkg: warning: downgrading fakeroot from 1.14.4-1ubuntu1 to  1.12.4ubuntu1.
Preparing to replace fakeroot 1.14.4-1ubuntu1 (using  .../fakeroot_1.12.4ubuntu1_i386.deb) ...
Unpacking replacement fakeroot ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.4.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.1-4ubuntu8_i386.deb) ...
Selecting previously deselected package libstdc++6-4.4-dev.
Unpacking libstdc++6-4.4-dev (from  .../libstdc++6-4.4-dev_4.4.1-4ubuntu8_i386.deb) ...
dpkg: warning: downgrading patch from 2.6-2ubuntu1 to 2.5.9-5.
Preparing to replace patch 2.6-2ubuntu1 (using  .../patch_2.5.9-5_i386.deb) ...
Unpacking replacement patch ...
Setting up dkms (2.1.0.1-0ubuntu1) ...
Installing new version of config file  /etc/dkms/template-dkms-mkdeb/debian/control ...
Installing new version of config file  /etc/dkms/template-dkms-mkdeb/debian/postinst ...
Installing new version of config file /etc/kernel/postinst.d/dkms ...
Installing new version of config file /etc/kernel/header_postinst.d/dkms  ...
 * Running DKMS auto installation service for kernel 2.6.32-23-generic                                                 [ OK ] 

Setting up fakeroot (1.12.4ubuntu1) ...

dpkg: dependency problems prevent configuration of g++-4.4:
 g++-4.4 depends on gcc-4.4-base (= 4.4.1-4ubuntu:cool:; however:
  Version of gcc-4.4-base on system is 4.4.3-4ubuntu5.
 g++-4.4 depends on gcc-4.4 (= 4.4.1-4ubuntu:cool:; however:
  Version of gcc-4.4 on system is 4.4.3-4ubuntu5.
dpkg: error processing g++-4.4 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libstdc++6-4.4-dev:
 libstdc++6-4.4-dev depends on gcc-4.4-base (= 4.4.1-4ubuntu:cool:; however:
  Version of gcc-4.4-base on system is 4.4.3-4ubuntu5.
 libstdc++6-4.4-dev depends on g++-4.4 (= 4.4.1-4ubuntu:cool:; however:
  Package g++-4.4 is not configured yet.
dpkg: error processing libstdc++6-4.4-dev (--install):
 dependency problems - leaving unconfigured
Setting up patch (2.5.9-5) ...
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.4 (>= 4.4.1-1); however:
  Package g++-4.4 is not configured yet.
dpkg: error processing g++ (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Setting up dpkg-dev (1.15.4ubuntu2) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up bcmwl-kernel-source (5.10.91.9+bdcom-0ubuntu4) ...
Adding Module to DKMS build system
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.32-23-generic  (i686)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/ for more information.
Installing initial module

Error! Could not locate wl.ko for module bcmwl in the DKMS tree.
You must run a dkms build for kernel 2.6.32-23-generic (i686) first.
Done.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Errors were encountered while processing:
 g++-4.4
 libstdc++6-4.4-dev
 g++







The package Broadcom STA Driver should now be installed!

All finished here! Reboot your system and you should have a working  WiFi...

I for the record, do not have working WiFi, It doesn't even show me my home network (or anybody else's) and now I have this lovely error. 

[IMG ATTACHED]

---

### Post by pytheas22 on 2010-07-13
Sorry those things didn't work.  But let's try one last time to install the STA driver before giving up and going down the ndiswrapper path.  Please run these commands, which should both fix the error message you're seeing in the top-right corner and install the STA driver another way:
```

sudo apt-get -f install
sudo apt-get install bcmwl-modaliases bcmwl-kernel-source
sudo rmmod b43
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
```

Any chance your wireless is up at this point?

---

### Post by idku on 2010-07-13
sudo apt-get -f install

> Installed. 

sudo apt-get install bcmwl-modaliases bcmwl-kernel-source

> Installed.

sudo rmmod b43

> ERROR: Module b43 does not exist in /proc/modules

sudo rmmod ssb

> ERROR: Module ssb does not exist in /proc/modules

sudo rmmod wl

> ERROR: Module wl does not exist in /proc/modules

sudo modprobe wl

> Nothing, simply gave me a new prompt.    

OH! The error thing in the top right corner is gone. Well... I call that progress!  lol

---

### Post by pytheas22 on 2010-07-13
That all looks good.  Even after a reboot, you don't have wireless?  What is the output after a reboot of:
```

sudo rmmod b43
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
dmesg | grep -e eth -e wlan -e wl
sudo iwlist scan
lshw -C Network
```

Sorry this is proving to be difficult, but thanks for your patience.

---

### Post by idku on 2010-07-13
Thank you for _YOUR_ patience... and i'll do all of that now.  :p

---

### Post by idku on 2010-07-13
Rebooted.
No wireless networks detected.
As per your instructions... 

sudo rmmod b43

> ERROR: Module b43 does not exist in /proc/modulessudo rmmod ssb

> ERROR: Module ssb does not exist in /proc/modulessudo rmmod wl

> ERROR: Module wl does not exist in /proc/modulessudo modprobe wl

> Nothing, gave me a new prompt.dmesg | grep -e eth -e wlan -e wl

> [   13.013680] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.082886] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.082909] wl 0000:01:00.0: setting latency timer to 64
[   13.185229] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   22.196495] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   24.478686] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   24.765225] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   29.242296] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   35.637207] eth0: no IPv6 routers present
[  335.657381] wl 0000:01:00.0: PCI INT A disabled
[  399.118572] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  399.118600] wl 0000:01:00.0: setting latency timer to 64
[  399.132864] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 sudo iwlist scan

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argumentlshw -C Network

> WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:17:5a:b4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:25:b3:61:3d:30
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A ip=192.168.2.9 latency=0 multicast=yes
       resources: irq:26 memory:febc0000-febfffff ioport:ec80(size=128)


And still... no wireless.  :(

---

### Post by pytheas22 on 2010-07-13
Everything looks alright, except that bit about "Failed to read scan data : Invalid argument."  That usually indicates that the wireless radio is turned off.  I don't mean to sound pedantic, but are you sure the wireless on your laptop is turned on via the hotkey (usually something like Fn+F2) or other switch that you use to turn it on?  If the switch doesn't seem to be working, you may want to check BIOS settings; sometimes those have a section with different options for the wireless radio and playing around with them can solve the problem.

You can also try turning on the wireless radio from the command line using:

```
sudo rfkill unblock all
```

If you're sure the wireless is enabled but the command "sudo iwlist scan" keeps on complaining about "Failed to read scan data," what is the output of:
```

dmesg | grep -ie radio -e wl
```

Also, what make and model of netbook is this?

---

### Post by idku on 2010-07-13
> **pytheas22 said:**
> I don't mean to sound pedantic, but are you sure the wireless on your laptop is turned on via the hotkey (usually something like Fn+F2) or other switch that you use to turn it on?  If the switch doesn't seem to be working, you may want to check BIOS settings; sometimes those have a section with different options for the wireless radio and playing around with them can solve the problem.

Um... Fn + F2 isn't the internet. There IS a switch that's been permanently 'ON' since I installed Ubuntu. As far as seeming pendantic, i've mentioned my utter ignorance to the entire system and situation, so i'll reiterate that and promise not to take anything personally.  lol

> You can also try turning on the wireless radio from the command line using:

sudo rfkill unblock allThis wanted my password, then gave me a new line.



dmesg | grep -ie radio -e wl

> 
[   13.013680] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.082886] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.082909] wl 0000:01:00.0: setting latency timer to 64
[  335.657381] wl 0000:01:00.0: PCI INT A disabled
[  399.118572] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  399.118600] wl 0000:01:00.0: setting latency timer to 64
Also, what make and model of netbook is this?

> [http://www.google.com/products/catalog?hl=en&q=HP+MINI+110+1020nr&um=1&ie=UTF-8&cid=17445124631438260257&ei=xCs9TO79AYG88ga5o9zUDg&sa=X&oi=product_catalog_result&ct=result&resnum=3&ved=0CD0Q8wIwAg&os=tech-specs](http://www.google.com/products/catalog?hl=en&q=HP+MINI+110+1020nr&um=1&ie=UTF-8&cid=17445124631438260257&ei=xCs9TO79AYG88ga5o9zUDg&sa=X&oi=product_catalog_result&ct=result&resnum=3&ved=0CD0Q8wIwAg&os=tech-specs)

---

### Post by myotiger on 2010-07-13
Thank you very much pytheas22, it work for me. Dell studio 1555, wireless 1397 wlan mini card. I got the same message as idfku mentioned but suddenly wireless connection wonderfully achieve.

---

### Post by pytheas22 on 2010-07-13
I've done some more reading on this.  I think the first thing to try is reinstalling the package that provides the driver; [some French people]("http://forum.ubuntu-fr.org/viewtopic.php?pid=3358986") say that helped them.  You can reinstall with:

```
sudo apt-get install --reinstall bcmwl-kernel-source
```

After that, please reboot and see if you have better luck connecting in wicd.

I also found some people reporting that udev flip-flops the wired and wireless interface names, which could also cause problems.  To make sure that's not happening, please post the output of:
```

ifconfig
ifconfig -a
iwconfig
rfkill list
```

**myotiger**: glad it works for someone!  What message were you getting before that you suddenly stopped getting?

---

### Post by idku on 2010-07-14
sudo apt-get install --reinstall bcmwl-kernel-source

> Installed, rebooted, still no wireless connections found.

ifconfig

> eth0      Link encap:Ethernet  HWaddr 00:25:b3:61:3d:30  
          inet addr:192.168.2.9  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::225:b3ff:fe61:3d30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:145805 (145.8 KB)  TX bytes:24843 (24.8 KB)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ifconfig -a

> eth0      Link encap:Ethernet  HWaddr 00:25:b3:61:3d:30  
          inet addr:192.168.2.9  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::225:b3ff:fe61:3d30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:145805 (145.8 KB)  TX bytes:24843 (24.8 KB)
          Interrupt:26 

eth1      Link encap:Ethernet  HWaddr 00:26:5e:17:5a:b4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

rfkill list

> No change, new prompt.

---

### Post by pytheas22 on 2010-07-14
Ah, it looks like the interface is simply down and needs to be brought up.  Do you get a list of networks if you type:
```

sudo ifconfig eth1 up
sudo iwlist scan
```

---

### Post by idku on 2010-07-14
Your first command simply required my password and gave a new prompt. The SECOND however... 

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :

[Insert all wireless networks in range here]

So... YAY! But Wcid still shows nothing... :confused:

---

### Post by pytheas22 on 2010-07-14
That's good that iwlist can see networks.  Wicd probably is trying to use the wrong interface.  Press the Preferences button in wicd, and make sure the wireless interface is set to "eth1".  Then try scanning again.  If it fails, run "sudo ifconfig eth1 up" to make sure the interface is up.  Hopefully this will be the last step in getting you online.

---

### Post by idku on 2010-07-14
I'm online. With no wires. :D

...that did the trick, renaming the wireless in Wcid > Preferences. Wcid now shows me all of the network connections in my area. 

Now, assuming it doesn't do anything too wonky (i'll be back if it does... ) i'll happily take my leave.  I'm so very appreciative of your time and patience, thank you very much Pytheas22. You've made me very happy!  

**Note : If my computer stays online for the next 24-36 hours without anything wonky (you know what I mean!) i'll happily rename the thread to [SOLVED] as protocol seems to require**

---

### Post by pytheas22 on 2010-07-14
Glad to hear it's finally working, and sorry it took a bit of struggling.  Also, kudos to bkratz, without whose suggestion of using the STA driver we may not have figured this out.

If you find that you have to enter the command "sudo ifconfig eth1 up" manually each time you reboot to get the wireless working, let me know and we can write a script to do that for you automatically.

Also note that in the future, if you ever reinstall Ubuntu on this netbook, getting the wireless running *should* be as simple as going to System>Administration>Hardware Drivers and enabling the STA driver.  Ubuntu should have prompted you to do this when you logged in for the first time, but obviously something got mixed up.

---

### Post by idku on 2010-07-14
> If you find that you have to enter the command "sudo ifconfig eth1 up" manually each time you reboot to get the wireless working, let me know and we can write a script to do that for you automatically.

No problem here, this doesn't happen, so all is well!

> Also note that in the future, if you ever reinstall Ubuntu on this netbook, getting the wireless running *should* be as simple as going to System>Administration>Hardware Drivers and enabling the STA driver.

Consider this noted. Thanks to everyone that helped! :D

---

### Post by idku on 2010-07-14
New issue... it decided to kick me offline and all of my wireless networks disappeared. 

I was online, everything was fine. I set down the computer, came back about 10 minutes later, and I was offline, it was trying to obtain an IP, it failed, and all of the networks vanished. 

What am I doing wrong here?  :confused:

---

### Post by idku on 2010-07-14
A few pages back you gave me things to post after a dropped connection, preemptively, here they are :

dmesg | tail -25

> [  864.928042] eth1: no IPv6 routers present
[  865.356039] eth0: no IPv6 routers present
[  865.430033] CPU0 attaching NULL sched-domain.
[  865.430046] CPU1 attaching NULL sched-domain.
[  865.453401] CPU0 attaching sched-domain:
[  865.453418]  domain 0: span 0-1 level SIBLING
[  865.453431]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[  865.453456]   domain 1: span 0-1 level MC
[  865.453467]    groups: 0-1 (cpu_power = 1178)
[  865.453490] CPU1 attaching sched-domain:
[  865.453499]  domain 0: span 0-1 level SIBLING
[  865.453510]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[  865.453533]   domain 1: span 0-1 level MC
[  865.453543]    groups: 0-1 (cpu_power = 1178)
[  866.816958] atl1c 0000:02:00.0: irq 26 for MSI/MSI-X
[  866.817278] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  877.108233] eth0: no IPv6 routers present
[  877.252210] eth1: no IPv6 routers present
[  919.843009] atl1c 0000:02:00.0: irq 26 for MSI/MSI-X
[  919.843110] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  920.054718] atl1c 0000:02:00.0: irq 26 for MSI/MSI-X
[  920.054796] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  922.139685] type=1503 audit(1279152729.879:15):  operation="open" pid=3064 parent=3048 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[  929.804067] eth1: no IPv6 routers present
[  930.940070] eth0: no IPv6 routers present

 dmesg | grep -e wlan -e b43

> New prompt, nothing 'new'

---

### Post by pytheas22 on 2010-07-14
That's strange.  I don't see anything in your log output about the dropped connection at all.  Since you're using wicd, however, I'm wondering if perhaps NetworkManager is interfering with the connection (assuming you still have NM installed).  If you run:
```

sudo /etc/init.d/network-manager stop
```

and then connect in wicd, is the connection more stable?  If so, you could delete NetworkManager so you won't have this problem anymore with:
```

sudo apt-get remove network-manager
```

---

### Post by idku on 2010-07-14
I ran that first command... and got this : 

> sudo: /etc/init.d/network-manager: command not found

---

### Post by idku on 2010-07-14
:( @ this computer

---

### Post by pytheas22 on 2010-07-15
ahhhh...I guess you don't have NetworkManager installed.  It's there by default, but you (or the system) may have uninstalled it when wicd was installed.

I don't know how much you have invested in the current system, but if I were you, I'd think about reinstalling at this point just to go back to a clean slate.  After reinstall, enable the wireless using the Hardware Drivers utility, and hopefully all will just work.

I'm out of ideas as to what specifically might be causing the connection to drop, but we've had you mucking around with so much that you may have changed something strange, and reinstalling from scratch should put it back in order.

I'll be at the beach tomorrow so may not respond right away, but I'll be back eventually.

---

### Post by idku on 2010-07-17
Everything has behaved for a couple of days now... i'm going to properly label the thread solved, and bid the ones who've helped me adieu. 

I'll be back if i've more questions, i'm sure.  :)

---

