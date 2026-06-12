---
title: "Network card UNCLAIMED | Intel Corp. 82573L"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by sparezgw on 2010-05-05
Hi,all

My laptop is IBM T60.
I just installed the Ubuntu 10.04, but the network card was unclaimed.


**$ sudo lshw -C network**
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ee000000-ee01ffff ioport:3000(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:ce:c4:39
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:31 memory:edf00000-edf00fff

**$ lspci -nn**
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X1400 [1002:7145]
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
15:00.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]

---

### Post by chili555 on 2010-05-05
This is supposed to use the driver module *e1000e*Let's try to load it and see what errors or warnings there are.```
sudo modprobe e1000e
dmesg | grep -e eth -e e100
```Thanks.

---

### Post by sparezgw on 2010-05-06
**$ dmesg|grep -e eth -e e100**
[    0.267811] pci 0000:01:00.0: reg 18 32bit mmio: [0xee100000-0xee10ffff]
[    0.268161] pci 0000:00:01.0: bridge 32bit mmio: [0xee100000-0xee1fffff]
[    0.346430] pci 0000:00:01.0:   MEM window: 0xee100000-0xee1fffff
[    0.346978] pci_bus 0000:01: resource 1 mem: [0xee100000-0xee1fffff]
[    0.918428] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.918432] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.918486] e1000e 0000:02:00.0: Disabling L1 ASPM
[    0.918510] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.918554] e1000e 0000:02:00.0: setting latency timer to 64
[    0.918766] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[    0.990779] e1000e 0000:02:00.0: PCI INT A disabled
[    0.990788] e1000e: probe of 0000:02:00.0 failed with error -5

This is the return, thanks...

---

### Post by chili555 on 2010-05-06
> e1000e 0000:02:00.0: Disabling L1 ASPMThis is what I am Googling now. I found this: [http://www.linuxquestions.org/questions/linux-hardware-18/problems-with-intel-gigabit-adapter-e1000e-driver-799934/](http://www.linuxquestions.org/questions/linux-hardware-18/problems-with-intel-gigabit-adapter-e1000e-driver-799934/)> ...the culprit was NetworkManager. I stumbled across it by accident when I got the traffic to pass again, then disabled it as a service, and all of the symptoms returned. After a bit of digging, I did the following to fix:

1. yum remove NetworkManager
2. edit /etc/resolv.conf to remove the comments NetworkManager put in there, and add back in the 'search domain.com' and 'nameserver w.x.y.z' statements.
3. reboot server, and all was well again, with no NetworkManager.

Thanks for all of the help - hope this helps someone else.Removing Network Manager may be an option, or maybe not. Let's try something first.```
sudo /etc/init.d/NetworkManager stop
sudo rmmod -f e1000e
sudo modprobe e1000e
dmesg | grep e1000e
```Does dmesg report success after 0.99?> [ [COLOR="Red"]0.99[/COLOR]0788] e1000e: probe of 0000:02:00.0 failed with error -5
I have seen the service described as NetworkManager or network-manager; you may have to try both.

---

### Post by sparezgw on 2010-05-07
I only have the service network-manager, and after stop the NetworkManager dmesg still reports errors.

[    0.839822] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.839825] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.839878] e1000e 0000:02:00.0: Disabling L1 ASPM
[    0.839904] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.839948] e1000e 0000:02:00.0: setting latency timer to 64
[    0.840235] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[    0.914819] e1000e 0000:02:00.0: PCI INT A disabled
[    0.914826] e1000e: probe of 0000:02:00.0 failed with error -5
[  760.888596] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[  760.888602] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[  760.888693] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  760.888751] e1000e 0000:02:00.0: setting latency timer to 64
[  760.889023] e1000e 0000:02:00.0: irq 32 for MSI/MSI-X
[  760.961716] e1000e 0000:02:00.0: PCI INT A disabled
[  760.961732] e1000e: probe of 0000:02:00.0 failed with error -5

---

### Post by chili555 on 2010-05-07
There is no improvement.

The next thing I suggest is to go here:  [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&lang=eng)

Download the latest version. I think downloads by default go to your Downloads folder. You will need to have build-essential and linux-headers-generic installed. Then do:```
cd ~/Downloads
tar zxf e1000e-1.1.19.tar.gz
cd e1000e-1.1.19/src/
sudo make install
sudo rmmod -f e1000e
sudo modprobe e1000e
dmesg | grep e100
```Is there any improvement?

---

### Post by sparezgw on 2010-05-07
No, nothing happens...


[    0.210823] pci 0000:01:00.0: reg 18 32bit mmio: [0xee100000-0xee10ffff]
[    0.211009] pci 0000:00:01.0: bridge 32bit mmio: [0xee100000-0xee1fffff]
[    0.276957] pci 0000:00:01.0:   MEM window: 0xee100000-0xee1fffff
[    0.277300] pci_bus 0000:01: resource 1 mem: [0xee100000-0xee1fffff]
[    0.825555] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.825559] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.825615] e1000e 0000:02:00.0: Disabling L1 ASPM
[    0.825640] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.825686] e1000e 0000:02:00.0: setting latency timer to 64
[    0.825900] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[    0.898821] e1000e 0000:02:00.0: PCI INT A disabled
[    0.898829] e1000e: probe of 0000:02:00.0 failed with error -5
[  116.197198] e1000e: Intel(R) PRO/1000 Network Driver - 1.1.19-NAPI
[  116.197205] e1000e: Copyright(c) 1999 - 2010 Intel Corporation.
[  116.197267] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  116.197326] e1000e 0000:02:00.0: setting latency timer to 64
[  116.197749] e1000e 0000:02:00.0: irq 32 for MSI/MSI-X
[  116.197774] e1000e 0000:02:00.0: ASPM disabled system-wide
[  116.269823] e1000e 0000:02:00.0: PCI INT A disabled
[  116.269839] e1000e: probe of 0000:02:00.0 failed with error -5

---

### Post by lbquy on 2010-05-14
Hi [sparezgw]("http://ubuntu-ky.ubuntuforums.org/member.php?u=279785") ,

I am using T60 and have same problem, are you resovable ? 

any one who can help me please ?

---

### Post by kevinyu on 2010-07-16
I met the same problem. Look forward to see your solution.

---

### Post by enemyben on 2010-08-18
Hey, anyone found a fix for this?  I'm in the same boat, Lenovo T60 just upgraded to Ubuntu 10.04, and no ethernet.  Thanks!

---

### Post by enemyben on 2010-08-18
SOLVED!  Follow the fantastic instructions of rreese6 on this page, worked for me.  Bit of a hassle to get ethernet up, but it works now!

[http://swiss.ubuntuforums.org/showthread.php?t=1276211&page=4](http://swiss.ubuntuforums.org/showthread.php?t=1276211&page=4)

---

### Post by StarlitxEyes on 2010-09-16
could this possibly help?  [http://intellinuxwireless.org/](http://intellinuxwireless.org/)
im giving it a try.. Im running Jolicloud on my Toshiba Satellite R10. My wireless is unclaimed as well :( hope this might work.

---

### Post by greenfinch on 2010-10-01
Hello everyone,

I'm also trying to get this card working. I hadn't have so much trouble with linux drivers for a long time. The driver for the wireless network (3945ABG) isn't much better. I'm using WEP at home now... 

I suppose you are talking about this fix:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1276211&page=4](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1276211&page=4)

I patched the intel e1000e-1.2.10 module but I'm still getting "NVM checksum not valid". I also tried the driver rreese6 used in his post from last year (e1000e-1.0.2.5.) but I didn't get further than a autoconf.h missing error. 

For the fun of it.. I then switched from Karmic to Maverick beta to check out if that's improving the wired ethernet. It didn't.

If anyone has more ideas... It would really be appreciated.



T60
Bios 2.26
linux 2.6.35-22-generic
Maverick


Intel Corp. 82573L
[77214.672443] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.10-NAPI
[77214.672451] e1000e: Copyright(c) 1999 - 2010 Intel Corporation.
[77214.672512] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[77214.672548] e1000e 0000:02:00.0: setting latency timer to 64
[77214.673503] e1000e 0000:02:00.0: irq 47 for MSI/MSI-X
[77214.673531] e1000e 0000:02:00.0: Disabling ASPM L0s 
[77214.736334] e1000e 0000:02:00.0: (unregistered net_device): The NVM Checksum Is Not Validx
[77214.736429] e1000e 0000:02:00.0: (unregistered net_device): Invalid MAC Address: 00:00:00:00:00:00
[77214.746711] e1000e 0000:02:00.0: PCI INT A disabled
[77214.746731] e1000e: probe of 0000:02:00.0 failed with error -5


  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:ee000000-ee01ffff ioport:2000(size=32)

---

### Post by greenfinch on 2010-10-01
I just tried the eeprom fix script from intel
[http://e1000.sourceforge.net/files/fixeep-82573-dspd.sh]("http://e1000.sourceforge.net/files/fixeep-82573-dspd.sh")

The script(/ethtool) wants an interface to work with.. However I don't know how to give ethtool an interface as long as the card is unclaimed.

ok right now I'm checking at the mailing-list archive how to hack the module that it allows bad checksums. Someone prepared code for that case but it looks like it didn't make it into the current version.

Is someone eager to help me with this? That would give me an actual interface to work with and this means I could apply the eeprom fix.

[http://lists-archives.org/linux-kernel/19744545-e1000e-allow-bad-checksum.html](http://lists-archives.org/linux-kernel/19744545-e1000e-allow-bad-checksum.html)

---

### Post by greenfinch on 2010-10-01
ok I'm writing now from my wired connection. :popcorn:

I was finally able to load the driver without any real eeprom or mac checks. Then I was able to configure the address with ifconfig. That was all. The eeprom fix wasn't applicable.

However the source now looks like a plucked chicken. I was frustrated.. This means I'm not going to publish it. But I will retrace my steps tomorrow and clean things up to post it here. Additionally I'm going to contact the intel e1000e devs. They should include a real option to load the e1000e module without any eeprom or further mac checks. 

The connection feels stable for now. gigabit, full duplex. finally :D


[88984.281176] e1000e 0000:02:00.0: PCI INT A disabled
[88984.484120] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.10-NAPI
[88984.484124] e1000e: Copyright(c) 1999 - 2010 Intel Corporation.
[88984.484183] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[88984.484213] e1000e 0000:02:00.0: setting latency timer to 64
[88984.484838] e1000e 0000:02:00.0: irq 47 for MSI/MSI-X
[88984.484861] e1000e 0000:02:00.0: Disabling ASPM L0s 
[88984.544405] e1000e 0000:02:00.0: (unregistered net_device): The NVM Checksum Is Not Valid
[88984.601804] e1000e 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:00:00:00:00:00
[88984.601812] e1000e 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[88984.601896] e1000e 0000:02:00.0: eth0: MAC: 3, PHY: 2, PBA No: 005301-003


  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:80:48:ba:d1:20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.2.10-NAPI firmware=0.5-1 ip=192.168.1.22 latency=0 multicast=yes
       resources: irq:47 memory:ee000000-ee01ffff ioport:2000(size=32)

---

### Post by i20234 on 2011-03-26
soab.... teh swiss deleted that post?! :confused::confused::confused::confused:

I was getting excited bc this is exactly my problem, please help!

---

### Post by i20234 on 2011-03-26
> **greenfinch said:**
> ok I'm writing now from my wired connection. :popcorn:

I was finally able to load the driver without any real eeprom or mac checks. Then I was able to configure the address with ifconfig. That was all. The eeprom fix wasn't applicable.

However the source now looks like a plucked chicken. I was frustrated.. This means I'm not going to publish it. But I will retrace my steps tomorrow and clean things up to post it here. Additionally I'm going to contact the intel e1000e devs. They should include a real option to load the e1000e module without any eeprom or further mac checks. 

The connection feels stable for now. gigabit, full duplex. finally :D


[88984.281176] e1000e 0000:02:00.0: PCI INT A disabled
[88984.484120] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.10-NAPI
[88984.484124] e1000e: Copyright(c) 1999 - 2010 Intel Corporation.
[88984.484183] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[88984.484213] e1000e 0000:02:00.0: setting latency timer to 64
[88984.484838] e1000e 0000:02:00.0: irq 47 for MSI/MSI-X
[88984.484861] e1000e 0000:02:00.0: Disabling ASPM L0s 
[88984.544405] e1000e 0000:02:00.0: (unregistered net_device): The NVM Checksum Is Not Valid
[88984.601804] e1000e 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:00:00:00:00:00
[88984.601812] e1000e 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[88984.601896] e1000e 0000:02:00.0: eth0: MAC: 3, PHY: 2, PBA No: 005301-003


  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:80:48:ba:d1:20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.2.10-NAPI firmware=0.5-1 ip=192.168.1.22 latency=0 multicast=yes
       resources: irq:47 memory:ee000000-ee01ffff ioport:2000(size=32)

Would apprecaite if you "But I will retrace my steps tomorrow and clean things up to post it here."

Thanks

---

### Post by sorcerer01 on 2011-07-01
issue probably solved, take a look at :

[http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/](http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/)

---

