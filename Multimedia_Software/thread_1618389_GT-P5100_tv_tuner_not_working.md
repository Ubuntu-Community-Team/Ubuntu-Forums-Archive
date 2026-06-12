---
title: "GT-P5100 tv tuner not working"
date: 2010-11-10
forum: Multimedia Software
---

### Post by MenestrelX on 2010-11-10
Hello,

I am trying to get a tv tuner type GT-P5100 to work in Kubuntu but I have no luck. 
The type of tv tunner is:
[http://www.gigabyte.com/products/product-page.aspx?pid=2781#sp](http://www.gigabyte.com/products/product-page.aspx?pid=2781#sp)

I checked [http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page) and there is no page for this kind of tuner. 

I've compiled [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) 
and it worked, but in tvtime I get no image.

Is there another way to test if my tv tuner is working ?

I have no entry in /dev/dvb

A relevant part of dmesg is:

[   12.783155] saa7130/34: v4l2 driver version 0.2.16 loaded
[   12.783200] saa7134 0000:04:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   12.783205] saa7133[0]: found at 0000:04:01.0, rev: 209, irq: 19, latency: 32, mmio: 0xfdbff000
[   12.783211] saa7133[0]: subsystem: 1458:9008, board: UNKNOWN/GENERIC [card=0,autodetected]
[   12.783293] saa7133[0]: board init: gpio is 40000

Please help :)

---

### Post by MenestrelX on 2010-11-17
nobody ? :(

---

