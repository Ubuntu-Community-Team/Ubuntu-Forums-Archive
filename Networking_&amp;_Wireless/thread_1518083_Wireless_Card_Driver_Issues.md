---
title: "Wireless Card Driver Issues"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by pheersmotu on 2010-06-26
I've got a Dell Inspiron 1525 with a Dell Wireless 1395 wlan mini-card. I'm new to Ubuntu, but I know that my problem with connecting is my driver. I tried getting it from the Broadcom website and I tried ndiswrapper. With both I was following the instructions on the read me files, but it says that either the locations do not exist or that it can't locate the files. Because I don't have internet on my Ubuntu, I've been downloading the files to a usb and trying to run them from there. Any help would be greatly appreciated. 
Thanks,
Pheersmotu

---

### Post by purelinuxuser on 2010-06-26
We'll need some debug information.  Open a Terminal and post the output of the following commands (since you can't post directly, just copy and paste to a text file and then move it to another computer):
```
lspci
lshw -c network
iwconfig
```
I recommend getting an Ethernet connection to your laptop.  It generally makes sorting out these kinds of problems a lot easier. ;)

---

### Post by pheersmotu on 2010-06-26
I actually tried using a wired connection earlier today. It recognized that it was there, but when I tried to configure it, it said that the source was unresponsive. I know it was working though, because of the Windows on my dual-booter. 

After typing in the commands you told me, I got:

```
*****@Pheersmotu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
*****@Pheersmotu:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e0:8b:4c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe7fc000-fe7fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:68:cb:e5:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*****@Pheersmotu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```I'm not sure if that's the best way to show you the response, but like I said I'm new at this.

While this is proving extremely difficult for me, I'm actually enjoying it in a twisted sort of way lol. Thanks endlessly for your help. I can't tell you how much I appreciate it. :)

---

### Post by purelinuxuser on 2010-06-27
> **pheersmotu said:**
> I actually tried using a wired connection earlier today. It recognized that it was there, but when I tried to configure it, it said that the source was unresponsive. I know it was working though, because of the Windows on my dual-booter.

That's weird.  Try disconnecting/reconnecting the cable.

As for your output, looks like you have a Broadcom BCM4312 wireless card.  The easiest way to install the driver for this thing is to plug into Ethernet, go to System > Administration > Hardware Drivers, and install the "Broadcom Proprietary STA" driver.  No need to go to Broadcom's site- nice, isn't it? :D

If you absolutely *cannot* get an Internet connection, try downloading and installing the following packages:
```
http://mirrors.us.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb
http://mirrors.us.kernel.org/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb
```> **pheersmotu said:**
> While this is proving extremely difficult for me, I'm actually enjoying it in a twisted sort of way lol. Thanks endlessly for your help. I can't tell you how much I appreciate it. :)

We all get that feeling! :lolflag:

---

### Post by pheersmotu on 2010-06-27
I downloaded the files you told me to on a usb drive and ran them in my Ubuntu. Tha first one installed fine, however the ```
bcmwl-kernel-source_5.60.48.36+bdcom-Oubuntu3_i386.deb
``` didn't install. I got the following message:

```
(Reading database ... 122807 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-21-generic
Building for architecture i686
Building initial module for 2.6.32-21-generic
/usr/sbin/dkms: line 35: patch command not found

Error! Application of patch 0001-Module_License.patch failed.
Check /car/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--install):
 subprocess installed post-installation script returned error exit status 6
Error were encountered when processing:
 bcml-kernel-source
```

---

### Post by purelinuxuser on 2010-06-27
Install this package: [http://mirrors.us.kernel.org/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb](http://mirrors.us.kernel.org/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb)

Then try to reinstall the second package (bcmwl-kernel-source).

---

### Post by pheersmotu on 2010-06-28
IT WORKED!!!! Thank you sooo much :)

---

### Post by purelinuxuser on 2010-06-28
> **pheersmotu said:**
> IT WORKED!!!! Thank you sooo much :)

You're welcome... and don't forget [SOLVED]. ;)

---

