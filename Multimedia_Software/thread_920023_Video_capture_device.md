---
title: "Video capture device"
date: 2008-09-14
forum: Multimedia Software
---

### Post by 73ckn797 on 2008-09-14
What video capture device(s) can be used with Ubuntu?

I do not care to watch TV on my computer. I only want to be able to capture from a video camera. If TV capability is a part of the product, that will be OK.

I have the Plextor PX-AV100U (USB) but I know it cannot be used, at least from the info that I have found so far.

Please pass along your recommendations.

---

### Post by cariboo on 2008-09-14
Check this page here:

[http://mythtv.org/wiki/index.php?title=Plextor_ConvertX&redirect=no](http://mythtv.org/wiki/index.php?title=Plextor_ConvertX&redirect=no)

It seems that your device is supported.

Jim

---

### Post by 73ckn797 on 2008-09-15
I followed the link provided but saw no specific info besides stating that it was uncertain if the device would work. 

I have connected the device but there is no recognition by the system of the device being connected, at least unlike the response when a flash drive is plugged in.

I have searched the forum but have not found anyone stating they have had success with the device. The Plextor site stated there was no Linux support for the device. That is why I stated the same in my original post.

I will go further into the link you provided later. It is time to get out and work!!

---

### Post by skullmunky on 2008-09-16
do you want live video or a camcorder?  i've found firewire (IEEE 1394) to be pretty reliable, in either case.

---

### Post by 73ckn797 on 2008-09-16
I will just be using a camcorder to copy video to the computer to burn to disk. These will be home videos and old, already converted to VHS, 8mm movies from the 50's and 60's.

I was aware of firewire but what device (make/brand) should I buy that will be compatible with Linux/Ubuntu? I do see that there are several TV cards but I need something with composite/RCA connection inputs.

---

### Post by skullmunky on 2008-09-22
I have a Panasonic PV-GS320.  It's a little MiniDV 3-CCD cam, and works fine.  It's actually overkill for what you need.  There's a very good chance that ANY mini DV videocamera that has firewire will work.  Most DV cameras also have analog composite inputs, so you can just plug your VCR into those and either record to mini-DV tape or just play it through directly over firewire to your computer. 

Choosing a TV tuner card or capture card seems to be a little trickier.  The reason is that digital video over firewire is a single, open standard, so almost all devices that support it will be compatible.  Capture cards and USB capture devices, on the other hand, all have their own unique drivers, which are usually closed-source.  So there you really have to do your research to see if someone has reverse-engineered a driver for the device.  The other term you want to put into google is "video4linux," which is the video input system for capture cards, tv tuners, webcams, and usb capture devices.

---

### Post by 73ckn797 on 2008-09-23
I am aware of the V4L but have not Googled it yet, or at least not recently so I do not remember any of the results. Short term memory loss ................... what was I going to say?

---

### Post by Perkins on 2008-10-16
To my knowledge, Ubuntu doesn't react to plugging in a camera or capture device like it does to a flash drive.  You won't see any pop-up messages or anything like that.

Start with XSane.  It recognizes several camera chipsets well enough to verify that they work.

After that, try Cheese.  It's a simple program, but seems to work rather well.

If that still doesn't get it for you, then things get more complicated.  Check and see if /dev/video0 exists.  If it does, then the system at least thinks it has a camera, and it may be worth getting some of the command-line capture programs which will let you figure out exactly what parameters your device supports.

---

### Post by cariboo on 2008-10-16
Try the V4L Wiki, they have a large list of supported devices.

[http://www.linuxtv.org/v4lwiki/index.php/Main_Page](http://www.linuxtv.org/v4lwiki/index.php/Main_Page)

Jim

---

### Post by 73ckn797 on 2008-11-15
> **cariboo907 said:**
> Try the V4L Wiki, they have a large list of supported devices.

[http://www.linuxtv.org/v4lwiki/index.php/Main_Page](http://www.linuxtv.org/v4lwiki/index.php/Main_Page)

Jim

I bookmarked the link and have looked it over, Thanks.

I installed a firewire pci card and it is recognized by the system:

lspci results:
```
01:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
```

lshw results:

 ```
*-firewire
             description: FireWire (IEEE 1394)
             product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
             vendor: VIA Technologies, Inc.
             physical id: 8
             bus info: pci@0000:01:08.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
```

I assume that I am doing well at this point.

I have one video camera (Sony Handycam DCR-HC3) that uses a firewire connection. It is a simple plug and play on my son's Vista box. I figure/hope that it will be the same in Ubuntu.

Another camera (Samsung SCL810) that uses a USB and/or composite connection which I will probably have to run through a capture device. We have the Pinnacle Movie Box but I have not tried it. It can connect with firewire to the computer with the camera going into the Movie Box. I will play around with it and let you know what happens. If successful I will also make sure to pass along the compatability, if any, to sources that would want to know.

Later.

---

### Post by DuncanNZ on 2009-02-23
Hi there, since you're having trouble with capture over Firewire to Kino you might want to look at my recent update of the [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) page. Please let me know if there are any problems with that guide.

---

### Post by 73ckn797 on 2009-02-24
I will look at that. Thanks.

---

