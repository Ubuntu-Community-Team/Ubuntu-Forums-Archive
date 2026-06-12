---
title: "ubuntu 9.10 wireless doesnt work"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by jhk30 on 2009-10-31
I am new to ubuntu.

ubuntu 9.04- sound didnt work. downgraded to 8.10 and sound and everything worked.

upgraded to 9.10 today and my wireless isnt being detected. It has a red light. (should be blue when detected)

HP Pavilion 1027ca

Thanks!

P.S. I AM BRAND NEW TO LINUX SO I DONT KNOW SUDO ECT.

---

### Post by Turtle.net on 2009-10-31
We will need more details than that ....
A lot of post are already talking about wireless issues after uprgrade to Karmic.
You could start by searching for the type of card you have
```
lshw -C network
```

---

### Post by jhk30 on 2009-10-31
```
joshua@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f0200000-f0203fff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:21:cc:37:c2:97
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:26 ioport:a000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)
joshua@ubuntu:~$ 


```

---

### Post by Turtle.net on 2009-10-31
A short research of "BCM4322" on this forum send me [here]("http://ubuntuforums.org/showthread.php?t=1305392") and the solution is explained in the post and [here]("http://swiss.ubuntuforums.org/showpost.php?p=8090292&postcount=1").

---

### Post by jhk30 on 2009-10-31
it says for me to insert the CD rom when trying to install that BCMWL-KERNAL-SOURCE from Package manager. and It is inserted. it even shows on desktop

---

### Post by nelamvr6 on 2009-10-31
This is one of the things that frustrates me about Ubuntu.

The LiveCD had the restricted drivers for my Broadcom wireless card available, so my wireless worked with the live CD.  On install though the restricted drivers were nowhere to be found. And so I had no wireless.  Pain in the ***.

Why doesn't Ubuntu do like Mint does and include the restricted drivers out of the gate?  Especially with things like wireless and video, where there's a good chance that the restricted drivers might be needed?

Ubuntu 9.10 is pretty nice, but Mint 8 will eat its lunch.  Guaranteed.

---

### Post by jhk30 on 2009-10-31
I have mint 8. but it doesnt show up in the boot menu (since I dual boot with win 7)

---

### Post by Turtle.net on 2009-10-31
> **nelamvr6 said:**
> This is one of the things that frustrates me about Ubuntu. Excuse me but you are not really helping, and eventhough Mint will with no doubt save humanity from doom, you are still off topic.

> **jhk30 said:**
> it says for me to insert the CD rom when trying to install that BCMWL-KERNAL-SOURCE from Package manager. and It is inserted. it even shows on desktop
I had the same problem the other day (unable to reproduce it though).
So, even if it's not really an answer, try to reboot and reproduce the process described [here]("http://swiss.ubuntuforums.org/showpost.php?p=8090292").
If the problem persists, try to access directly the drive and browse the files in it. Find bcmwl-kernel-source and copy it to /var/cache/apt/archives and then go to synaptic and retry to install it.

---

### Post by Crucias on 2009-11-01
I have tried the fix suggested by Turtle.net but i am on a netbook, i cannot insert a cd. I installed off the live usb. The driver worked properly on the live image. This is kinda silly to be having this problem now.

(Exact problem is no ethernet or wireless drivers work, and prop drivers wont activate)

HP Mini 1000

---

### Post by JBAlaska on 2009-11-01
You need to have the box checked in software sources that says "Installable from CD-ROM" then it should fetch stuff off the CD-ROM when you apt-get

---

### Post by Crucias on 2009-11-01
problem is all i have is a usb port

---

### Post by Turtle.net on 2009-11-01
Ok don't panic.
You just have to let your system think that you already downloaded the package. If you installed from a liveUSB then the packages needed should be on this USB key.
Locate the bcmwl-kernel-source package on your usb key. then copy it to /var/cache/apt/archives (you need root privileges, so you should use the command line).
You may also need the dkms, linux-libc-dev, libc6-dev and linux-headers-generic packages.
Do the same trick and launch synaptic, install bcmwl-kernel-source and that should be ok.

---

### Post by lpeter on 2009-11-02
2 Nov 09 	 	 	 	 	  

 New guy.
 

 Toshiba Laptop L515, installed 9.04, no joy on wireless, waited for 9.10, still no joy.   Have plowed through the various postings and to the best of my (admittedly) limited ability have not been able to effect resolution (i.e. wireless connection) with the various procedures outlined.  

I would be very grateful for any assistance.  

From reading the various postings, I've learned that there are several different terminal commands normally requested in order to give a better understanding of the machine.  Those details follow:
 **lpeter@pscaai:~$ sudo ifconfig -a ** 
 eth0 Link encap:Ethernet HWaddr 00:1e:33:cd:71:b1  
 inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0  
 inet6 addr: fe80::21e:33ff:fecd:71b1/64 Scope:Link  
 UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1  
 RX packets:5426 errors:0 dropped:0 overruns:0 frame:0  
 TX packets:3373 errors:0 dropped:0 overruns:0 carrier:0  
 collisions:0 txqueuelen:1000  
 RX bytes:2107802 (2.1 MB) TX bytes:517979 (517.9 KB)  
 Interrupt:28 Base address:0xe000  
 lo Link encap:Local Loopback  
 inet addr:127.0.0.1 Mask:255.0.0.0  
 inet6 addr: ::1/128 Scope:Host  
 UP LOOPBACK RUNNING MTU:16436 Metric:1  
 RX packets:78 errors:0 dropped:0 overruns:0 frame:0  
 TX packets:78 errors:0 dropped:0 overruns:0 carrier:0  
 collisions:0 txqueuelen:0  
 RX bytes:9069 (9.0 KB) TX bytes:9069 (9.0 KB)  
 

 **lpeter@pscaai:~$ sudo cat /etc/network/interfaces ** 
 # This file describes the network interfaces available on your system  
 # and how to activate them. For more information, see interfaces(5).  
 # The loopback network interface  
 auto lo  
 iface lo inet loopback  
 # The primary network interface  
 auto eth0  
 #iface eth0 inet dhcp  
 

 **lpeter@pscaai:~$ sudo lshw -C network ** 
 *-network  
 description: Ethernet interface  
 product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller  
 vendor: Realtek Semiconductor Co., Ltd. 
 physical id: 0  
 bus info: pci@0000:02:00.0  
 logical name: eth0  
 version: 02  
 serial: 00:1e:33:cd:71:b1  
 size: 100MB/s  
 capacity: 100MB/s  
 width: 64 bits  
 clock: 33MHz  
 capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
 configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100MB/s  
 resources: irq:28 ioport:4000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)  
 *-network UNCLAIMED  
 description: Network controller  
 product: Realtek Semiconductor Co., Ltd.  
 vendor: Realtek Semiconductor Co., Ltd. 
 physical id: 0  
 bus info: pci@0000:03:00.0  
 version: 01  
 width: 32 bits  
 clock: 33MHz  
 capabilities: pm msi pciexpress bus_master cap_list  
 configuration: latency=0  
 resources: ioport:2000(size=256) memory:d4600000-d4603fff  
 

 **lpeter@pscaai:~$ sudo ifconfig ** 
 eth0 Link encap:Ethernet HWaddr 00:1e:33:cd:71:b1  
 inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0  
 inet6 addr: fe80::21e:33ff:fecd:71b1/64 Scope:Link  
 UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1  
 RX packets:5658 errors:0 dropped:0 overruns:0 frame:0  
 TX packets:3412 errors:0 dropped:0 overruns:0 carrier:0  
 collisions:0 txqueuelen:1000  
 RX bytes:2157833 (2.1 MB) TX bytes:522000 (522.0 KB)  
 Interrupt:28 Base address:0xe000  
 lo Link encap:Local Loopback  
 inet addr:127.0.0.1 Mask:255.0.0.0  
 inet6 addr: ::1/128 Scope:Host  
 UP LOOPBACK RUNNING MTU:16436 Metric:1  
 RX packets:78 errors:0 dropped:0 overruns:0 frame:0  
 TX packets:78 errors:0 dropped:0 overruns:0 carrier:0  
 collisions:0 txqueuelen:0  
 RX bytes:9069 (9.0 KB) TX bytes:9069 (9.0 KB)  
 

 **lpeter@pscaai:~$ sudo iwlist scan ** 
 lo Interface doesn't support scanning.  
 eth0 Interface doesn't support scanning.  
 

 **lpeter@pscaai:~$ sudo cat /etc/modprobe.d/blacklist ** 
 cat: /etc/modprobe.d/blacklist: No such file or directory  
 

 **lpeter@pscaai:~$ sudo lsmod ** 
 Module Size Used by  
 ecb 2524 1  
 binfmt_misc 8356 1  
 ppdev 6688 0  
 snd_hda_codec_realtek 203328 1  
 snd_hda_intel 26920 2  
 snd_hda_codec 75708 2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep 7200 1 snd_hda_codec  
 snd_pcm_oss 37920 0  
 snd_mixer_oss 16028 1 snd_pcm_oss  
 snd_pcm 75296 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 sha256_generic 11580 0  
 snd_seq_dummy 2656 0  
 aes_i586 8124 556  
 snd_seq_oss 28576 0  
 snd_seq_midi 6432 0  
 snd_rawmidi 22208 1 snd_seq_midi  
 aes_generic 27484 1 aes_i586  
 snd_seq_midi_event 6940 2 snd_seq_oss,snd_seq_midi  
 snd_seq 50224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 cbc 3516 554  
 usblp 12636 0  
 ath_pci 203476 0  
 snd_timer 22276 2 snd_pcm,snd_seq  
 wlan 226416 1 ath_pci  
 snd_seq_device 6920 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 ath_hal 303104 1 ath_pci  
 iptable_filter 3100 0  
 snd 59204 16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 ip_tables 11692 1 iptable_filter  
 uvcvideo 59080 0  
 soundcore 7264 1 snd  
 psmouse 56180 0  
 dm_crypt 12928 1  
 lp 8964 0  
 snd_page_alloc 9156 2 snd_hda_intel,snd_pcm  
 x_tables 16544 1 ip_tables  
 videodev 36736 1 uvcvideo  
 serio_raw 5280 0  
 parport 35340 2 ppdev,lp  
 joydev 10272 0  
 v4l1_compat 14496 2 uvcvideo,videodev  
 fbcon 36640 72  
 tileblit 2460 1 fbcon  
 font 8124 1 fbcon  
 bitblit 5372 1 fbcon  
 softcursor 1756 1 bitblit  
 usbhid 38208 0  
 usb_storage 52544 0  
 i915 220872 3  
 drm 159584 3 i915  
 i2c_algo_bit 5760 1 i915  
 video 19380 1 i915  
 output 2780 1 video  
 r8169 32064 0  
 mii 5212 1 r8169  
 intel_agp 27484 2 i915  
 agpgart 34988 2 drm,intel_agp  
 

 **lpeter@pscaai:~$ sudo uname -r ** 
 2.6.31-13-generic  
 

 **lpeter@pscaai:~$ sudo uname -r ** 
 2.6.31-13-generic  
 lpeter@pscaai:~$ sudo dmesg | grep -e ath -e wlan  
 [ 4.765095] device-mapper: multipath: version 1.1.0 loaded  
 [ 4.765097] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [ 19.807694] ath_hal: module license 'Proprietary' taints kernel.  
 

 **lpeter@pscaai:~$ sudo cat /etc/lsb-release**  
 DISTRIB_ID=Ubuntu  
 DISTRIB_RELEASE=9.10  
 DISTRIB_CODENAME=karmic  
 DISTRIB_DESCRIPTION="Ubuntu 9.10" 
 

 **lpeter@pscaai:~$ sudo uname -a ** 
 Linux pscaai 2.6.31-13-generic #45-Ubuntu SMP Tue Oct 13 02:08:03 UTC 2009 i686 GNU/Linux  
 

 **lpeter@pscaai:~$ sudo lspci -vvnnn -s 02:00.**0  
 02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)  
 Subsystem: Toshiba America Info Systems Device [1179:ff1e]  
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+  
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-  
 Latency: 0, Cache Line Size: 32 bytes  
 Interrupt: pin A routed to IRQ 28  
 Region 0: I/O ports at 4000 [size=256]  
 Region 2: Memory at d0410000 (64-bit, prefetchable) [size=4K]  
 Region 4: Memory at d0400000 (64-bit, prefetchable) [size=64K]  
 Expansion ROM at d0420000 [disabled] [size=128K]  
 Capabilities: [40] Power Management version 3  
 Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)  
 Status: D0 PME-Enable- DSel=0 DScale=0 PME-  
 Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+  
 Address: 00000000fee0300c Data: 4199  
 Capabilities: [70] Express (v2) Endpoint, MSI 01  
 DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us  
 ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-  
 DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-  
 RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-  
 MaxPayload 128 bytes, MaxReadReq 4096 bytes  
 DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-  
 LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us  
 ClockPM+ Suprise- LLActRep- BwNot-  
 LnkCtl: ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+  
 ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-  
 LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-  
 Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2  
 Vector table: BAR=4 offset=00000000  
 PBA: BAR=4 offset=00000800  
 Capabilities: [cc] Vital Product Data <?>  
 Capabilities: [100] Advanced Error Reporting <?>  
 Capabilities: [140] Virtual Channel <?> 
 Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-01  
 Kernel driver in use: r8169  
 Kernel modules: r8169  
 

 **lpeter@pscaai:~$ sudo dmidecode ** 
 # dmidecode 2.9  
 SMBIOS 2.4 present.  
 35 structures occupying 1524 bytes.  
 Table at 0x000E8130.  
 Handle 0x0000, DMI type 0, 24 bytes  
 BIOS Information  
 Vendor: INSYDE  
 Version: 1.20  
 Release Date: 07/03/2009  
 ROM Size: 1024 kB  
 Characteristics:  
 PCI is supported  
 BIOS is upgradeable  
 BIOS shadowing is allowed  
 Boot from CD is supported  
 Selectable boot is supported  
 BIOS ROM is socketed  
 EDD is supported  
 Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)  
 Japanese floppy for Toshiba 1.2 MB is supported (int 13h)  
 5.25"/360 KB floppy services are supported (int 13h)  
 5.25"/1.2 MB floppy services are supported (int 13h)  
 3.5"/720 KB floppy services are supported (int 13h)  
 3.5"/2.88 MB floppy services are supported (int 13h)  
 8042 keyboard services are supported (int 9h)  
 CGA/mono video services are supported (int 10h)  
 ACPI is supported  
 USB legacy is supported  
 Targeted content distribution is supported  
 Handle 0x0001, DMI type 1, 27 bytes  
 System Information  
 Manufacturer: TOSHIBA  
 Product Name: Satellite L515  
 Version: PSLF2U-00S00L  
 Serial Number: 79161440Q  
 UUID: 79BD9A50-6386-11DE-BBA9-001E33CD71B1  
 Wake-up Type: Power Switch  
 SKU Number: Montevina_Fab  
 Family: Intel_Mobile  
 Handle 0x0002, DMI type 2, 16 bytes  
 Base Board Information  
 Manufacturer: TOSHIBA  
 Product Name: Portable PC  
 Version: Base Board Version  
 Serial Number: Base Board Serial Number 
 Asset Tag: Base Board Asset Tag  
 Features:  
 Board is a hosting board  
 Board is replaceable  
 Location In Chassis: Base Board Chassis Location  
 Chassis Handle: 0x0003  
 Type: Motherboard  
 Contained Object Handles: 0  
 Handle 0x0003, DMI type 3, 22 bytes  
 Chassis Information  
 Manufacturer: Chassis Manufacturer  
 Type: Notebook  
 Lock: Not Present  
 Version: Chassis Version  
 Serial Number: Chassis Serial Number  
 Asset Tag: No Asset Tag  
 Boot-up State: Safe  
 Power Supply State: Safe  
 Thermal State: Safe  
 Security Status: None  
 OEM Information: 0x00000000  
 Height: Unspecified  
 Number Of Power Cords: 1  
 Contained Elements: 0  
 Handle 0x0004, DMI type 5, 20 bytes  
 Memory Controller Information  
 Error Detecting Method: None  
 Error Correcting Capabilities:  
 None  
 Supported Interleave: One-way Interleave  
 Current Interleave: One-way Interleave  
 Maximum Memory Module Size: 4096 MB  
 Maximum Total Memory Size: 8192 MB  
 Supported Speeds:  
 Other  
 Supported Memory Types:  
 Other  
 Memory Module Voltage: Unknown  
 Associated Memory Slots: 2  
 0x0000  
 0x0000  
 Enabled Error Correcting Capabilities:  
 None  
 Handle 0x0005, DMI type 9, 13 bytes  
 System Slot Information  
 Designation: J6B2  
 Type: x16 PCI Express  
 Current Usage: Available  
 Length: Other  
 ID: 0  
 Characteristics:  
 PME signal is supported  
 Hot-plug devices are supported  
 Handle 0x0006, DMI type 9, 13 bytes  
 System Slot Information  
 Designation: J6B1  
 Type: x1 PCI Express  
 Current Usage: Available  
 Length: Other  
 ID: 0  
 Characteristics:  
 PME signal is supported  
 Hot-plug devices are supported  
 Handle 0x0007, DMI type 9, 13 bytes  
 System Slot Information  
 Designation: J6C2  
 Type: x1 PCI Express  
 Current Usage: Available  
 Length: Other  
 ID: 1  
 Characteristics:  
 PME signal is supported  
 Hot-plug devices are supported  
 Handle 0x0008, DMI type 9, 13 bytes  
 System Slot Information  
 Designation: J7B1  
 Type: x1 PCI Express  
 Current Usage: Available  
 Length: Other  
 ID: 2  
 Characteristics:  
 PME signal is supported  
 Hot-plug devices are supported  
 Handle 0x0009, DMI type 9, 13 bytes  
 System Slot Information  
 Designation: J8B3  
 Type: x1 PCI Express  
 Current Usage: Available  
 Length: Other  
 ID: 3  
 Characteristics:  
 PME signal is supported  
 Hot-plug devices are supported  
 Handle 0x000A, DMI type 9, 13 bytes  
 System Slot Information  
 Designation: J8D1  
 Type: x1 PCI Express  
 Current Usage: Available  
 Length: Other  
 ID: 4  
 Characteristics:  
 PME signal is supported  
 Hot-plug devices are supported  
 Handle 0x000B, DMI type 11, 5 bytes  
 OEM Strings  
 String 1: PSLF2U-00S00L,TI100680V0E,13Q01  
 String 2: EitllYifvm25+  
 String 3: ocffeH6VKAd6q  
 String 4: Sz5gbycbTUATc  
 String 5:  
 Handle 0x000C, DMI type 12, 5 bytes  
 System Configuration Options  
 Option 1: NVR:00707002  
 Option 2: DSN:090612PB4C00QYH1MMSA  
 Option 3: DSN:M4 70T5663EH3-CF7 859F8F00  
 Option 4: DSN:7A567466  
 Handle 0x000D, DMI type 15, 29 bytes  
 System Event Log  
 Area Length: 32672 bytes  
 Header Start Offset: 0x0000  
 Data Start Offset: 0x0000  
 Access Method: General-purpose non-volatile data functions  
 Access Address: 0x0000  
 Status: Valid, Not Full  
 Change Token: 0x12345678  
 Header Format: OEM-specific  
 Supported Log Type Descriptors: 3  
 Descriptor 1: POST memory resize  
 Data Format 1: None  
 Descriptor 2: POST error  
 Data Format 2: POST results bitmap  
 Descriptor 3: Log area reset/cleared  
 Data Format 3: None  
 Handle 0x000E, DMI type 21, 7 bytes  
 Built-in Pointing Device  
 Type: Touch Pad  
 Interface: PS/2  
 Buttons: 4  
 Handle 0x000F, DMI type 27, 14 bytes  
 Cooling Device  
 Type: Fan  
 Status: OK  
 OEM-specific Information: 0x00000000  
 Nominal Speed: 43690 rpm  
 Handle 0x0010, DMI type 32, 20 bytes  
 System Boot Information  
 Status: No errors detected  
 Handle 0x0011, DMI type 39, 22 bytes  
 System Power Supply  
 Location: OEM_Define0  
 Name: OEM_Define1  
 Manufacturer: OEM_Define2  
 Serial Number: OEM_Define2  
 Asset Tag: OEM_Define3  
 Model Part Number: OEM_Define4  
 Revision: OEM_Define5  
 Max Power Capacity: 0.075 W  
 Status: Present, OK  
 Type: Regulator  
 Input Voltage Range Switching: Auto-switch  
 Plugged: No  
 Hot Replaceable: No  
 Handle 0x0012, DMI type 129, 5 bytes  
 OEM-specific Type  
 Header and Data:  
 81 05 12 00 4F  
 Strings:  
 em Test 1  
 Oem Test 2  
 Handle 0x0013, DMI type 16, 15 bytes  
 Physical Memory Array  
 Location: System Board Or Motherboard  
 Use: System Memory  
 Error Correction Type: None  
 Maximum Capacity: 8 GB  
 Error Information Handle: No Error  
 Number Of Devices: 2  
 Handle 0x0014, DMI type 6, 12 bytes  
 Memory Module Information  
 Socket Designation: DIMM0  
 Bank Connections: 0 0  
 Current Speed: 1 ns  
 Type: None  
 Installed Size: 2048 MB (Single-bank Connection)  
 Enabled Size: 2048 MB (Single-bank Connection)  
 Error Status: OK  
 Handle 0x0015, DMI type 17, 27 bytes  
 Memory Device  
 Array Handle: 0x0013  
 Error Information Handle: 0x0016  
 Total Width: 64 bits  
 Data Width: 64 bits  
 Size: 2048 MB  
 Form Factor: SODIMM  
 Set: None  
 Locator: DIMM0  
 Bank Locator: BANK 0  
 Type: DDR2  
 Type Detail: Synchronous  
 Speed: 800 MHz (1.2 ns)  
 Manufacturer: Samsung  
 Serial Number: 859F8F26  
 Asset Tag: Unknown  
 Part Number: 262626262626262626262626262626262626  
 Handle 0x0016, DMI type 18, 23 bytes  
 32-bit Memory Error Information  
 Type: OK  
 Granularity: Unknown  
 Operation: Unknown  
 Vendor Syndrome: Unknown  
 Memory Array Address: Unknown  
 Device Address: Unknown  
 Resolution: Unknown  
 Handle 0x0017, DMI type 20, 19 bytes  
 Memory Device Mapped Address  
 Starting Address: 0x00000000000  
 Ending Address: 0x0007FFFFFFF  
 Range Size: 2 GB  
 Physical Device Handle: 0x0015  
 Memory Array Mapped Address Handle: 0x001D  
 Partition Row Position: Unknown  
 Interleave Position: 1  
 Interleaved Data Depth: 1  
 Handle 0x0018, DMI type 6, 12 bytes  
 Memory Module Information  
 Socket Designation: DIMM2  
 Bank Connections: 0 0  
 Current Speed: 1 ns  
 Type: None  
 Installed Size: 2048 MB (Single-bank Connection)  
 Enabled Size: 2048 MB (Single-bank Connection)  
 Error Status: OK  
 Handle 0x0019, DMI type 17, 27 bytes  
 Memory Device  
 Array Handle: 0x0013  
 Error Information Handle: 0x001A  
 Total Width: 64 bits  
 Data Width: 64 bits  
 Size: 2048 MB  
 Form Factor: SODIMM  
 Set: None  
 Locator: DIMM2  
 Bank Locator: BANK 2  
 Type: DDR2  
 Type Detail: Synchronous  
 Speed: 800 MHz (1.2 ns)  
 Manufacturer: Samsung  
 Serial Number: 859F9222  
 Asset Tag: Unknown  
 Part Number: 222222222222222222222222222222222222  
 Handle 0x001A, DMI type 18, 23 bytes  
 32-bit Memory Error Information  
 Type: OK  
 Granularity: Unknown  
 Operation: Unknown  
 Vendor Syndrome: Unknown  
 Memory Array Address: Unknown  
 Device Address: Unknown  
 Resolution: Unknown  
 Handle 0x001B, DMI type 20, 19 bytes  
 Memory Device Mapped Address  
 Starting Address: 0x00000000000  
 Ending Address: 0x0007FFFFFFF  
 Range Size: 2 GB  
 Physical Device Handle: 0x0019  
 Memory Array Mapped Address Handle: 0x001D  
 Partition Row Position: Unknown  
 Interleave Position: 2  
 Interleaved Data Depth: 1  
 Handle 0x001C, DMI type 18, 23 bytes  
 32-bit Memory Error Information  
 Type: OK  
 Granularity: Unknown  
 Operation: Unknown  
 Vendor Syndrome: Unknown  
 Memory Array Address: Unknown  
 Device Address: Unknown  
 Resolution: Unknown  
 Handle 0x001D, DMI type 19, 15 bytes  
 Memory Array Mapped Address  
 Starting Address: 0x00000000000  
 Ending Address: 0x000FFFFFFFF  
 Range Size: 4 GB  
 Physical Array Handle: 0x0013  
 Partition Width: 0  
 Handle 0x001E, DMI type 4, 35 bytes  
 Processor Information  
 Socket Designation: CPU  
 Type: Central Processor  
 Family: Pentium M  
 Manufacturer: Intel(R) Corporation  
 ID: 7A 06 01 00 FF FB EB BF  
 Signature: Type 0, Family 6, Model 23, Stepping 10  
 Flags:  
 FPU (Floating-point unit on-chip)  
 VME (Virtual mode extension)  
 DE (Debugging extension)  
 PSE (Page size extension)  
 TSC (Time stamp counter)  
 MSR (Model specific registers)  
 PAE (Physical address extension)  
 MCE (Machine check exception)  
 CX8 (CMPXCHG8 instruction supported)  
 APIC (On-chip APIC hardware supported)  
 SEP (Fast system call)  
 MTRR (Memory type range registers)  
 PGE (Page global enable)  
 MCA (Machine check architecture)  
 CMOV (Conditional move instruction supported)  
 PAT (Page attribute table)  
 PSE-36 (36-bit page size extension)  
 CLFSH (CLFLUSH instruction supported)  
 DS (Debug store)  
 ACPI (ACPI supported)  
 MMX (MMX technology supported)  
 FXSR (Fast floating-point save and restore)  
 SSE (Streaming SIMD extensions)  
 SSE2 (Streaming SIMD extensions 2)  
 SS (Self-snoop)  
 HTT (Hyper-threading technology)  
 TM (Thermal monitor supported)  
 PBE (Pending break enabled)  
 Version: Pentium(R) Dual-Core CPU T4300 @ 2.10GHz  
 Voltage: 1.6 V  
 External Clock: 800 MHz  
 Max Speed: 2100 MHz  
 Current Speed: 1200 MHz  
 Status: Populated, Enabled  
 Upgrade: <OUT OF SPEC>  
 L1 Cache Handle: 0x0021  
 L2 Cache Handle: 0x001F  
 L3 Cache Handle: Not Provided  
 Serial Number: Not Specified  
 Asset Tag: FFFF  
 Part Number: Not Specified  
 Handle 0x001F, DMI type 7, 19 bytes  
 Cache Information  
 Socket Designation: Unknown  
 Configuration: Enabled, Not Socketed, Level 2  
 Operational Mode: Write Back  
 Location: Internal  
 Installed Size: 1024 KB  
 Maximum Size: 1024 KB  
 Supported SRAM Types:  
 Synchronous  
 Installed SRAM Type: Synchronous  
 Speed: Unknown  
 Error Correction Type: Single-bit ECC  
 System Type: Unified  
 Associativity: 4-way Set-associative  
 Handle 0x0020, DMI type 7, 19 bytes  
 Cache Information  
 Socket Designation: Unknown  
 Configuration: Enabled, Not Socketed, Level 1  
 Operational Mode: Write Back  
 Location: Internal  
 Installed Size: 32 KB  
 Maximum Size: 32 KB  
 Supported SRAM Types:  
 Synchronous  
 Installed SRAM Type: Synchronous  
 Speed: Unknown  
 Error Correction Type: Single-bit ECC  
 System Type: Instruction  
 Associativity: 8-way Set-associative  
 Handle 0x0021, DMI type 7, 19 bytes  
 Cache Information  
 Socket Designation: Unknown  
 Configuration: Enabled, Not Socketed, Level 1  
 Operational Mode: Write Back  
 Location: Internal  
 Installed Size: 32 KB  
 Maximum Size: 32 KB  
 Supported SRAM Types:  
 Synchronous  
 Installed SRAM Type: Synchronous  
 Speed: Unknown  
 Error Correction Type: Single-bit ECC  
 System Type: Data  
 Associativity: 8-way Set-associative  
 Handle 0x0022, DMI type 127, 4 bytes  
 End Of Table

---

### Post by jhk30 on 2009-11-02
Ok so I found the problem. or fix...

Connect pc/laptop with a ethernet cable. (I did mine from router)
System> Administation> Hardware Drivers

It should find some (mine found broadcom B43 wireless driver & Broadcom STA wireless driver)

Click on it. click Activate, Type password. It will say "Downloading and Installing"

NOW. it just sits. doesnt download or install.. no progress. Started it about 10 times now.

---

