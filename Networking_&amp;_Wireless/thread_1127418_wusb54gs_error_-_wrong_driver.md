---
title: "wusb54gs error - wrong driver?"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by oneearth on 2009-04-16
sorry to start a new thread about the wusb54gs but i'm one of those frustrated souls whose wusb54gs v1 did not get nicely detected by intrepid. i searched the existing threads and incorporated what i could of their suggestions. the wusb54gs.inf, rndismp.sys, and usb8023.sys files i got from my dual boot windows xp installation which was using the wusb54gs to access the internet just fine:

 - running fresh install of 8.10 intrepid. when i booted 8.10 up the first time with the wusb54gs connected to a usb port, bootup hung on the "starting bluetooth" stage. i had to do physical reset to unhang it.

 - added ndiswrapper-util 1.9 and ndisgtk from the 8.10 cd

 - ran the windows wireless adapter and used the wusb54gs v1 driver that i downloaded from the linksys website and which has been working in windows xp. once i added rndismp.sys and usb8023.sys in /etc/ndiswrapper/wusb54gs (which i also got from windows xp), the windows wireless adapter shows wusb54gs as valid. when i plugged in the wusb54gs, it shows hardware "yes".


dmesg shows an error. do i have the wrong wusb54gs inf file? this newbie would appreciate any insight from the more experienced. i'm at work right now, and won't be back to the machine until later in the afternoon.

thx,


> 
h@h-desktop:~/Documents/linksys_wusb54gs_drivers$ ndiswrapper -l
wusb54gs : driver installed
	device (13B1:000E) present (alternate driver: rndis_wlan)

h@h-desktop:~/Documents/linksys_wusb54gs_drivers$ sudo depmod -a
h@h-desktop:~/Documents/linksys_wusb54gs_drivers$ sudo modprobe ndiswrapper

h@h-desktop:~/Documents/linksys_wusb54gs_drivers$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:29:f0:ea:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

h@h-desktop:~/Documents/linksys_wusb54gs_drivers$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

h@h-desktop:~/Documents/linksys_wusb54gs_drivers$ dmesg | grep ndiswrapper

[  385.153449] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  385.193807] usbcore: registered new interface driver ndiswrapper
[  491.165114] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisIMNotifyPnPEvent'
[  491.165221] ndiswrapper (load_sys_files:206): couldn't prepare driver 'wusb54gs'
[  491.166786] ndiswrapper (load_wrap_driver:108): couldn't load driver wusb54gs; check system log for messages from 'loadndisdriver'




---

