---
title: "Wireless Card not detected - Toshiba i5010"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by lordbux on 2011-06-18
Hai guys

I am faced with bit of a trouble here, 
I bought a new TOSHIBA C660 - i5010 today and installed
Lucid Lynx 10.04 on it, but it has not detected my wirelessg broadcom 80211 (STA) driver debp interface. 

[B]Output of lspci
[/B]
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

**Output for lsusb**
```
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

then searching on the web i came to find 
Broadcom Wireless STA driver (wl) Ubuntu 9.10/10.04 which i think is the driver which is required

I followed the instructions here ==> [http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)

But again there was trouble.:icon_frown:
The code would not compile

**output for make:**
```
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/grandmaster/Downloads/hybrid-portsrc_x86_32-v5_100_82_38/src/wl/sys/wl_linux.o
/home/grandmaster/Downloads/hybrid-portsrc_x86_32-v5_100_82_38/src/wl/sys/wl_linux.c:35:27: error:  linux/sched.h : No such file or directory
make[2]: *** [/home/grandmaster/Downloads/hybrid-portsrc_x86_32-v5_100_82_38/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/grandmaster/Downloads/hybrid-portsrc_x86_32-v5_100_82_38] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [all] Error 2

```:-(

and when i give this command as per instructed i get another error:
command : ```
udo mv wl.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
```:frown:

error: ```
mv: cannot stat `wl.ko': No such file or directory

```:confused:

So can someone please help me correct this issue or install the driver if at all it will help.

As i am leaving for college day after tomorrow i need to quickly find a solution please  help me, thanks in advance.:popcorn:

---

### Post by chili555 on 2011-06-18
Can you get a temporary wired ethernet connection and do:```
sudo apt-get install bcmwl-kernel-source dkms
sudo modprobe wl
```Now does your wireless rock?

---

