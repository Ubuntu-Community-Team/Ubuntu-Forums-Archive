---
title: "Upgrade to Karmic = dead wireless"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by beenie57 on 2009-11-05
I was using Jaunty 64bit with no problems and sine the online upgrade have has major wireless issues. My comp is HP Pavilion Slimline S3370 AMD Athlon 64 X2 processor 5000+, 2GB RAM, 320GB HDD, ATI Radeon HD 2400 PRO Graphic card and belkin 8051 usb adaptor. I've been trying to sort it out using the forums but can't make any progress. I've included some test results for you guys to look at :-

  	 	 	 	 	 	  ndiswrapper -l 
 WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
 

 netr28ux : driver installed 
 	device (050D:805C) present (alternate driver: rt2800usb) 
 

 

 lsusb 
 Bus 001 Device 003: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader 
 Bus 001 Device 002: ID 050d:805c Belkin Components  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 

 dmesg | grep -e ndis -e wlan 
 [    6.395395] ndiswrapper version 1.55 loaded (smp=yes, preempt=no) 
 [    7.376799] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool' 
 [    7.376812] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList' 
 [    7.376829] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver' 
 [    7.376835] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver' 
 [    7.376845] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl' 
 [    7.376858] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx' 
 [    7.376864] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool' 
 [    7.376870] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists' 
 [    7.376877] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete' 
 [    7.376885] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool' 
 [    7.376891] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool' 
 [    7.376897] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList' 
 [    7.376910] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority' 
 [    7.376916] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx' 
 [    7.376922] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes' 
 [    7.376928] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl' 
 [    7.376943] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind' 
 [    7.376947] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind' 
 [    7.376950] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netr28ux' 
 [    7.377485] ndiswrapper (load_wrap_driver:108): couldn't load driver netr28ux; check system log for messages from 'loadndisdriver' 
 [    7.377529] usbcore: registered new interface driver ndiswrapper
 

 lshw -C Network 
 WARNING: you should run this program as super-user. 
 

 contents of /etc/network
 

 auto lo 
 iface lo inet loopback 
 

 

 sudo ifconfig wlan0 up 
 [sudo] password for david:  
 wlan0: ERROR while getting interface flags: No such device 
 

 iwlist scan 
 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
 

 sudo rutilt 
 sudo: rutilt: command not found 
 

 locate ssb.ko 
 /lib/modules/2.6.31-14-generic/kernel/drivers/ssb/ssb.ko 
 

 ifconfig wlan0 
 wlan0: error fetching interface information: Device not found 
 

I am connected via wired at the moment but want to go back to wireless ASAP. When I right click network icon top right of the screen the enable wireless isn't appearing which it did in Jaunty. Any help would be much appreciated.

many thanks Beenie57

---

### Post by beenie57 on 2009-11-08
Bump.


No-one able to help me out??

---

