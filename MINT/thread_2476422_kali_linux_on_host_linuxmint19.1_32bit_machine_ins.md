---
title: "kali linux on host linuxmint19.1 32bit machine install fails"
date: 2022-06-25
forum: MINT
---

### Post by t-anderson58 on 2022-06-25
Here is my Machine:
  Type: Laptop System: Hewlett-Packard product: Presario V6000 (RZ330UA#ABA) 
  v: Rev 1 serial: <root required> 
  Mobo: Quanta model: 30D3 v: 65.3A serial: <root required> BIOS: Hewlett-Packard 
  v: F.1F date: 12/05/2007 

Here is my System:
  Host: presarioV6000 Kernel: 4.15.0-188-generic i686 bits: 32 
  Desktop: Cinnamon 4.0.10 Distro: Linux Mint 19.1 Tessa 

Here is my  CPU:
  Topology: Single Core model: Mobile AMD Sempron 3500+ bits: 64 type: UP 
  L2 cache: 512 KiB 
  Speed: 800 MHz min/max: 800/1800 MHz Core speed (MHz): 1: 800 
Partition:
  ID-1: / size: 50.58 GiB used: 14.78 GiB (29.2%) fs: ext4 dev: /dev/sda6 

VBoxManage list [--long|-l] [--sorted|-s] vms|runningvms|ostypes|hostdvds|hostfloppies|
                            intnets|bridgedifs|hostonlyifs|natnets|dhcpservers|
                            hostinfo|hostcpuids|hddbackends|hdds|dvds|floppies|
                            usbhost|usbfilters|systemproperties|extpacks|
                            groups|webcams|screenshotformats


VBoxManage  list extpacks
Extension Packs: 1
Pack no. 0:   VNC
Version:      5.2.42
Revision:     137960
Edition:      
Description:  VNC plugin module
VRDE Module:  VBoxVNC
Usable:       true 
Why unusable:

The kali linux boots into the virtualbox splash screen and the UEFI Grub menu with Graphical Install or Install options
both do not work I get an unexpected machine stop or crash with a message to visit virtualbox,org/community or forums
but the distro version of my virtualbox is  VirtualBox Graphical User Interface Version 5.2.42_Ubuntu r137960
 © 2004-2020 Oracle Corporation (Qt5.9.5

ubuntu which is a software package shiped with linuxmint19.1

---

### Post by guiverc on 2022-06-25
FYI:  You've placed this is a Ubuntu area of UbuntuForums; but no mention of Ubuntu is made.  Your host OS appears to be Linux Mint, with VM being Kali Linux.

Ubuntu and [*flavors*]("https://ubuntu.com/download/flavours") of Ubuntu areruntime *adjustment* free, as when changes need to be made, new packages are built.  Linux Mint *devs* don't have Ubuntu upload privileges, but wish to use Ubuntu packages; thus rely onruntime *adjustments*.  They're unlikely to be involved with your issue, but you're not using Ubuntu or *flavor* of Ubuntu, but a different software stack.

---

### Post by QIII on 2022-06-26
Moved to MINT.

---

### Post by TheFu on 2022-06-26
Using a 32-bit OS as a VM host will be very limiting. Only 32-but guests can be run and there isn't any VT-x or AMD-v hardware support. 

I'd say you should download the ubuntuforums system-information script, run that so we get a clear picture of the actual hardware, not some marketing data or model numbers that don't mean anything to everyone here.

[https://github.com/UbuntuForums](https://github.com/UbuntuForums) has the script.

Or run **inxi -Fxxz** and post that wrapped in code tags.  The system is from 2007, so it is fairly old and slow for running virtual machines.  A $75 chromebook would be faster and more capable.

As for getting help with Kali, most of the software in Kali can be used for cracking, which we cannot discuss here.

 > ubuntu which is a software package shiped with linuxmint19.1 
This is incorrect.  Ubuntu is an OS.  Mint is an OS.  They are not shipped inside each other.

---

