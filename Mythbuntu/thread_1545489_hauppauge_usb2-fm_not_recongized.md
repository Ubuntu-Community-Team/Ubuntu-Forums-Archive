---
title: "hauppauge usb2-fm not recongized"
date: 2010-08-03
forum: Mythbuntu
---

### Post by slack42 on 2010-08-03
Hi,

  I just did a clean install of mythbuntu 10.04 on a new system and I choose a hauppague wintv-usb2-fm because my motherboard doesn't have a pci slot, it's a Gigabyte H55N-USB3  board. I thought I saw that this tuner was supported and it seems to be a older device so I figured it would work but mythbuntu doesn't seem to see it. 

In mythbackend setup under capture cards the probed info says "Failed to open" and when I do lsusb is shows "Hauppauge" but that's the only indication of it being seen. Am I wrong in thinking that this usb tuner was supported? I've searched the forums but I can't find any info on my particular tuner. I've spent the last few days searching google as well but I still have come up with nothing. It's not the same as the wintv-pvr-usb2 that I've seen, here is a link to the usb tuner I have.

[http://tinyurl.com/28xark7](http://tinyurl.com/28xark7)

Any advice on how to get this working or even what driver it should be using would be greatly appreciated.

---

### Post by LowSky on 2010-08-04
can you show us the complete output of the results of the command lsusb, it will give the driver name. More than likely you just need the firmware, Also It seems you picked up a very very old usb tuner. EDIT: BUT according to [THIS]("http://www.linuxtv.org/wiki/index.php/Hauppauge") that tuner is not supported under Linux. 


If you need a tuner that works the Hauppauge WinTV-HVR-950Q is supported very well
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16815116034](http://www.newegg.ca/Product/Product.aspx?Item=N82E16815116034)
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q)

---

### Post by slack42 on 2010-08-04
Here is the output of lsusb but as you point out it looks like it's not supported.

```
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0734 Microsoft Corp. Wireless Optical Desktop 700
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 001 Device 002: ID 2040:b110 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I think I got it mixed up with the wintv-pvr-usb2 before I bought it on the compatibility list:(. I was looking at the one you mentioned before but it was quite a bit more but it looks like I might have to go that way if I can't find anything else that will do. Thanks for the info.

---

