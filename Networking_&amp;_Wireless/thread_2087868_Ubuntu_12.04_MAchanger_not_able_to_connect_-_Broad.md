---
title: "Ubuntu 12.04 MAchanger not able to connect - Broadcom BCM4313"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by First Last on 2012-11-24
Okay guys, So i've looked around extensively on this such  topic, Only to find that no one has a true solution, Only half explained  work arounds. Something tells me this problem can be solved for the  pure reason that i " CAN " change my wifi-cards MAC address in windows 7  both manually and using Iron Geeks madMACS. So thus leads me to  investigate why after changing my mac on ubuntu  10.04/10.10/12.04/Backtrack 5 r2/r3 why i cannot connect. 
  

Please not that this is not a case of my router i have tried it on  multiple public access and with my changed MAC i cannot even connect to a  open network,


 I've read somewhere that you have to change the mac  before the wifi-card's true MAC is released in BIOS. Is this true ? This  is the only logical explanation i can think of rite now. 
  I don't mind going out and buying a new wifi-card that does support  ubuntu MAC cloning. If any one has one working out of the box please let  me know. [INDENT]   [B]description: Wireless interface          product: BCM4313 802.11b/g/n Wireless LAN Controller

vendor: Broadcom Corporation [/B]      [B]

physical id: 0 

bus info: pci@0000:02:00.0     logical 

name: wlan0

version: 01     

serial: c0:18:85:43:c6:e4     

width: 64 bits 

clock: 33MHz 

capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless     

configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-29-generic-pae firmware=N/A ip=10.1.1.8 latency=0       link=yes multicast=yes wireless=IEEE 8 '[/B]
 [/INDENT]I have tried both Network-Manager & WICD both failing.
  Im using Acer Aspire D-270, First off i couldn't even change my MAC  address got the error of device busy etc. But then i added the macchange  to startup now the mac changes but it just wont connect till i set it  back to original mac.

---

### Post by chili555 on 2012-11-24
Are you asking over at askubuntu.com? See my comment there.

---

### Post by First Last on 2012-11-25
Hi there Chilli, 

Just saw your post on AskUbuntu. Thanks for trying to help out i've replied back to you just now. Incase you see this first i was pretty much saying that i understand what you mean when you say you don't think it is a MAC problem rather than a driver issue, But my biggest confusion is that i can only connect to networks when im using my REAL MAC address. I'm aware of all possibilities like my router may be only assigning 1 IP address to 1 MAC address, But that's not the case, Even when i go to coffee shops and free public wifi's i can ONLY connect with my original MAC address. When i change mac it just keeps prompting for password or just sits their trying to connect.

Thankyou once again for your fast replies and curtousy to help out

---

### Post by chili555 on 2012-11-25
I know *nothing* about MAC changing. I do know, based on lots and lots of experience on three Linux forums, that brcmsmac is not optimal if your device is 14e4:4727. Broadcom STA is optimal. If you'd like to change, do:```
lspci  -nn
```Verify you have 14e4:4727. Then do:```
sudo apt-get install linux-headers-gemeric bcmwl-kernel-source
sudo modprobe wl
```Obviously, it's your choice.

---

### Post by First Last on 2012-11-26
Okay great ! , I'm ready to change the driver. I trust what you say i'll give it a go i've got not much to lose.

> ubuntu@ubuntu:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.2.0-33 linux-headers-3.2.0-33-generic
The following NEW packages will be installed:
  linux-headers-3.2.0-33 linux-headers-3.2.0-33-generic linux-headers-generic
0 upgraded, 3 newly installed, 0 to remove and 231 not upgraded.
1 not fully installed or removed.
Need to get 12.7 MB of archives.
After this operation, 67.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-headers-3.2.0-33 all 3.2.0-33.52 [11.7 MB]
Get:2 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-headers-3.2.0-33-generic i386 3.2.0-33.52 [975 kB]
Get:3 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-headers-generic i386 3.2.0.33.36 [2638 B]
Fetched 12.7 MB in 23s (536 kB/s)                                              
Selecting previously unselected package linux-headers-3.2.0-33.
(Reading database ... 151510 files and directories currently installed.)
Unpacking linux-headers-3.2.0-33 (from .../linux-headers-3.2.0-33_3.2.0-33.52_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-33-generic.
Unpacking linux-headers-3.2.0-33-generic (from .../linux-headers-3.2.0-33-generic_3.2.0-33.52_i386.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.33.36_i386.deb) ...
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
lzma: (stdin): Cannot allocate memory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-headers-3.2.0-33 (3.2.0-33.52) ...
Setting up linux-headers-3.2.0-33-generic (3.2.0-33.52) ...
Setting up linux-headers-generic (3.2.0.33.36) ...
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot
0 upgraded, 3 newly installed, 0 to remove and 231 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1363 kB of archives.
After this operation, 3908 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously unselected package dkms.
(Reading database ... 173809 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_i386.deb) ...
Processing triggers for man-db ...
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
lzma: (stdin): Cannot allocate memory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-29-generic-pae
Building for architecture i686
Building initial module for 3.2.0-29-generic-pae
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-29-generic-pae/updates/dkms/

depmod.......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
lzma: (stdin): Cannot allocate memory
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Errors were encountered while processing:
 initramfs-tools
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ sudo modprobe wl
ubuntu@ubuntu:~$ lspci-nn
lspci-nn: command not found
ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller [8086:0bf1] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)

  

But it's still showing my wireless as  [14e4:4727]  ?

---

### Post by chili555 on 2012-11-26
> lzma: (stdin): Cannot allocate memory
dpkg: error processing initramfs-tools (--configure):
subprocess installed post-installation script returned error exit status 1Oops!

We have to overcome whatever this is and try again. Unfortunately, it seems that your system ran out of memory when trying to install a package update. Please copy off these instructions so that you can close out your browser and *every* program you are running. Open a terminal and run:```
sudo apt-get update
sudo apt-get upgrade
```Were there any problems or errors along the way? If so, stop and post them here. If not, take one step at a time:```
sudo apt-get install --reinstall initramfs-tools
``````
sudo apt-get install linux-headers-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~. Next step:```
sudo apt-get install linux-headers-generic
```If everything is still OK, do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```If, at any time, you see an error, stop and post it here.> But it's still showing my wireless as [14e4:4727] ?Yes, and it always will be. However, when we're done, the driver will have changed from b43 to wl and the interface will have changed from wlan0 to eth1. 

You will be able to connect much better.

---

