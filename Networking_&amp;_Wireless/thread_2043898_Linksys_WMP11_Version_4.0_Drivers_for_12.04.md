---
title: "Linksys WMP11 Version 4.0 Drivers for 12.04"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by Philip11 on 2012-08-17
First of all I know WMP11 is rather old Hardware but anyway I tried using NDISwrapper I installed the Windows driver it says the hardware is present but the wireless doesn't work

My Specs
Motherboard NF61V-M2 V1.0
AMD Athlon 64 4200+ X2@2.2GHz
1GB RAM
Running Ubuntu Studio 12.04

And a Screenshot of NDISWrapper
[IMG]http://i48.tinypic.com/b5ju44.png[/IMG]
And when I do lspci I get

00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a2)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6100 nForce 400] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Ethernet controller: InProComm Inc. IPN 2120 802.11b


Thanks! :)

---

### Post by Philip11 on 2012-08-18
*Bump*

---

### Post by chili555 on 2012-08-18
Please open a terminal and run and post:```
sudo modprobe ndiswrapper
lspci -nn | grep 0280
ndiswrapper -l
dmesg | grep ndis
```Thanks.

---

### Post by Philip11 on 2012-08-18
> **chili555 said:**
> Please open a terminal and run and post:```
sudo modprobe ndiswrapper
lspci -nn | grep 0280
ndiswrapper -l
dmesg | grep ndis
```Thanks.
modprobe ndiswrapper Gives me: FATAL: Module ndiswrapper not found.
lspci -nn | grep 0280 Gives me: nothing
ndiswrapper -l Gives me: 

lsbcmnds : driver installed
lsipnds : driver installed
    device (17FE:2120) present
wmp11nds : driver installed

dmesg | grep ndis: Prints nothing

---

### Post by chili555 on 2012-08-18
> modprobe ndiswrapper Gives me: FATAL: Module ndiswrapper not found.Yikes! Not again! Please get a wired ethernet connection and do:```
sudo apt-get install ndiswrapper-dkms
```When it's done, detach the ethernet and try again:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Thanks.

---

### Post by Philip11 on 2012-08-19
> **chili555 said:**
> Yikes! Not again! Please get a wired ethernet connection and do:```
sudo apt-get install ndiswrapper-dkms
```When it's done, detach the ethernet and try again:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Thanks.

sudo modprobe ndiswrapper:  prints nothing

dmesg | grep ndis: prints

[  242.224065] ndiswrapper version 1.57 loaded (smp=yes, preempt=yes)
[  242.346140] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  242.346145] ndiswrapper (load_sys_files:199): couldn't prepare driver 'lsipnds'
[  242.346184] ndiswrapper (load_wrap_driver:121): couldn't load driver 'lsipnds'
[  242.346285] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2012-08-19
> ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010BDo you think you can find the .inf file for Windows XP and 64-bit? I haven't found it yet.

Of course, and I know this is radical, you could re-install a 32-bit version of Ubuntu or buy any number of supported devices for US$12-15.

---

### Post by Philip11 on 2012-08-19
> **chili555 said:**
> Do you think you can find the .inf file for Windows XP and 64-bit? I haven't found it yet.

Of course, and I know this is radical, you could re-install a 32-bit version of Ubuntu or buy any number of supported devices for US$12-15.
I already had Internet although I don't get that great of a signal with the USB Adapter I'm using I was thinking I could get a better signal with this thanks anyway! :guitar:

And considering Windows XP was never 64 Bit then you'll have a very hard time doing that :P

---

