---
title: "'eth1' instead of 'usb0'"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by Ganesh de on 2011-06-07
I am working on USB Connectivity between android 2.1 Host and Windows Mobiles 6.1 device...When I connect the windows mobile device to android host through USB (in RNDIS Mode), It is appearing as 'eth1' interface instead of 'usb0' interface.
Why 'eth1' instead of 'usb0' ?
Does behaviour of 'eth1' is same as 'usb0'?
 
Case 1: I connected my Samsung Galaxy I7500 phone (android phone) to my Host (android) through USB Cable. It was in ECM Mode.It is detecting as 'usb0' device.
 
Case 2: I connected Windows Mobile to my Host(android) through USB Cable.It was in RNDIS Mode.It is detecting as 'eth1' device.
 
Being both phones connected through USB Cable, Why windows phone is detecting as 'eth1' device?
 
[ECM and RNDIS are one and the same.]
 
Result of 'ifconfig'
 
eth1 Link encap:Ethernet HWaddr 80:00:60:0f:e8:00 
inet addr:169.254.2.2 Bcast:169.254.2.255 Mask:255.255.255.0
inet6 addr: fe80::8200:60ff:fe0f:e800/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:14 errors:7 dropped:0 overruns:0 frame:0
TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1264 (1.2 KB) TX bytes:5477 (5.4 KB)
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
 
Thanks in advance,
 
Regards,
Ganesh

---

### Post by doas777 on 2011-06-07
[NDIS]("http://en.wikipedia.org/wiki/Network_Driver_Interface_Specification") is a network stack component for windows network drivers, and is an interface that applications can use to operate a network connection. it allows any application to use any NDIS capable network card, without actually knowing what kind of card it is.

for one reason or other, the developers have chosen to emulate a network connection instead of using a USB driver interface as your other phone does. then they use the USB networking interface to pass the connection over the USB cable.

using a network emulated connection would allow them to use the same component for connecting if the data source was an actual network connection (perhaps for internet enabled features) so that would be my guess as to why they did it that way.

as you can see [here]("http://www.thesycon.de/eng/usb_cdcecm.shtml"), the USB stack uses ECM at a lower level than NDIS, so it may be that one phone is directly accessing teh ECM layer and the other uses NDIS (which in turn uses ECM).

---

### Post by Ganesh de on 2011-06-07
Thanks for your reply...

I need some more information...
Actually, emulation of ethernet interface over USB interface means all the data passing through 'eth1' will pass through USB interface internally... Is it right?

My Issue is,
I am working on multicasting through 'usb0'  and 'eth1' interface...I tried with samsung phone which creates 'usb0' interface and multicasting is supported for 'usb0' interface...

And I also tried with windows mobiles phone which creates 'eth1' interface (Uses RNDIS) 
If 'eth1' is emulated over 'usb' interface means why not multicasting is not supported 'eth1' interface...

Is it the problem with eth1 driver (virtual interface driver) in android host or some thing else?

Please reply me...

Thanks in advance,

Regards,
Ganesh

---

