---
title: "Can someone recommend me a USB Network Device?"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by Jaymoid on 2006-02-04
Hi All,

I currently have a us robotics 5422 usb wifi device, which I can't seem to get working in ubuntu. So I'm after a small, fuss-free device - that works with ubuntu/ndiswrapper easily, or even better, works with ubuntu (breezy) natively. 

Oh yeah, it has to be one of the g (54mbps) ones please.

Thanks, all advice is appreciated. 

James

---

### Post by hajk on 2006-02-04
If you find one of those "fuss-free" devices, then I would like to know too...

Am using a SpeedTouch 121g device right now, which requires ndiswrapper and the Windows driver BT4501G. For them to work properly, I needed to download the ndiswrapper 1.8 source from SourceForge and compile it; and I downloaded the latest BT4501G driver files from SpeedTouch. The setup works most of the time, but sometimes (after a day or so, it varies...) I need to restart (by unloading/reloading ndiswrapper) or even to reboot (when the system just freezes). Don't know whether this is due to ndiswrapper/bt4501g, or due to another of my own errors. :confused: 

So, yes, a fuss-free "g" USB device, please!

---

### Post by Jaymoid on 2006-02-06
[QUOTE=hajk]If you find one of those "fuss-free" devices, then I would like to know too...
...
So, yes, a fuss-free "g" USB device, please![/QUOTE]

My housemate has a toshiba laptop, which has wifi built in and it worked with hoary right from the install cd! I've tried finding out which chipset it uses, but no luck.

I actually emailed us robotics the other day and got a response from them today about this. Here is their reply:
> 
USRobotics does not normally offer Linux device support,
and unfortunately I cannot determine the nature of the Ndiswrapper (which I am
aware that some customers use this driver for some of our network adapters). 
There are several sources for support, regarding the Ndiswrapper drivers - that
may be your best option for receiving support that is specific to these
third-party Linux drivers:
[http://ndiswrapper.sourceforge.net/support.html](http://ndiswrapper.sourceforge.net/support.html)




On a seperate note, I may try your route and download the latest ndiswrapper version and try that. Thanks for the reply. If anyone else has any good devices to recommend, that would be muchly appreciated.

Ta.

---

