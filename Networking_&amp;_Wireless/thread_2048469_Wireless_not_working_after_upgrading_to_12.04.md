---
title: "Wireless not working after upgrading to 12.04"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by panorack on 2012-08-26
I've just upgraded to 12.04 on my Dell Studio but the wireless is not connecting. The settings seem ok and I've checked it in Windows 7 and it is working ok on that system.

There is a wireless key on the Dell for quick switching of the wireless on and off but there is no response from toggling this in Ubuntu (although it is working ok in Windows 7). All the other function keys are showing a response, eg. battery status, brightness etc. so I can only assume that the upgrade has shut down the wireless. Problem is, if this is so, how can I activate it again if the wireless key is not responding?

If anyone has any ideas I would be very grateful. 


Many thanks in advance,

---

### Post by bakegoodz on 2012-08-26
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by panorack on 2012-08-28
Thanks for that bakegoodz. Have worked through some of the commands listed and show the ones I think are relevant. 

1. lspci -nn | grep 'Wireless Brand' gives no output in terminal
2. iwconfig gives the following error message:
lo        no wireless extensions.

eth0      no wireless extensions.

The wireless module is working as shown by booting Windows 7. lspci and ifconfig don't mean much to me but I have shown the output below in case it is any help. Please let me know if  you need further info re system.

output from lspci:
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
07:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
07:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
07:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
07:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

output from ifconfig:
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:4c:db:73  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f24d:a2ff:fe4c:db73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2070656 (2.0 MB)  TX bytes:296357 (296.3 KB)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12200 (12.2 KB)  TX bytes:12200 (12.2 KB)


Hope this is of use, and many thanks

---

### Post by Finnicella on 2012-08-28
Did you try to leave the swith of the wifi turned on in windows and then see if it works in Ubuntu? 
Bye

---

### Post by panorack on 2012-09-03
Didn't get anywhere with the above so decided to backup and do a fresh install of 12.04. This worked ok with wireless working. Interestingly, after downloading all updates as at beginning of Sept. Wireless still working ok. Presume earlier problems with Network Manager have been addressed.

---

