---
title: "Oneiric support for ATSC TV?"
date: 2011-10-27
forum: Multimedia Software
---

### Post by jcoles on 2011-10-27
The Digital TV Control Centre looks like the tool you would need to configure a DTV card, but it has no ATSC (North American DTV) support. I installed MeTV, but it simply reports "There are no DVB devices available" and provides no means to configure one. 

TV Time also has no ATSC support. (NTSC is obsolete!) And when I start it, nothing happens.

Are North Americans completely out of luck for DTV apps? 

Has anyone got an ATSC TV card, internal or USB to work in Oneiric?
How?

---

### Post by wolfen69 on 2011-10-27
First we need to know what tv tuner you have. Also, I can assure you NTSC still works in ubuntu, as I am from the US, and my Hauppauge PVR150 works just fine.

---

### Post by jcoles on 2011-10-27
The device is a WinTV-HVR 950e. The Additional Drivers utility shows the Auvitek AU0828 drivers present and activated. 

If you are from the US, then you know that NTSC (analog!) TV was discontinued and replaced with ATSC a couple of years ago. 

With MeTV clueless about hardware configuration, I tried installing the scantv utility. It asks for the "TV norm", but offers only NTSC-M. In earlier versions of Ubuntu, scantv supported many standards, including ATSC. A big step backwards here. The utility reports errors
ioctl: VIDIOC_S_CTRL(id=9963778;value=128): Invalid argument
ioctl: VIDIOC_S_CTRL(id=9963776;value=109): Invalid argument
ioctl: VIDIOC_S_CTRL(id=9963779;value=0): Invalid argument
ioctl: VIDIOC_S_CTRL(id=9963777;value=121): Invalid argument
pauses, and eventually quits. Adding a symbolic link from /dev/vbi0 to /dev/vbi has enabled it to search NTSC channels (there are none) but the errors remain. 

The Digital TV control centre looks like the ideal configuration tool, but the first thing it tells you is that ATSC is not supported. Major shortcoming.

Does it take some ugly command line hacking to set this up? I'm up to it, but most casual computer users are not. 

Can you give me any clues? Would any of the How-to articles for earlier releases be applicable? I was hoping that Oneiric would show some technical progress.

Thanks.

---

### Post by wolfen69 on 2011-10-27
Have you tried any other tv viewing apps? There's TVtime and Xawtv for you to try. Sometimes they will *just work*.

---

### Post by wolfen69 on 2011-10-27
[Here]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950#Making_it_Work") is the linux tv wiki for your tuner. I'm almost positive you can get it going. Be patient.

---

### Post by jcoles on 2011-10-29
My device is a HVR-950Q. The Wiki had a cross-reference to its page. Apparently, the firmware is already included in Ubuntu. But something was still missing. 
After installing w_scan and performing a scan with it, I was able to get Me-TV to recognize and scan the device. 
There is never more than a garbled picture and no sound. So, I'm back to my previous experience with HDTV under Ubuntu -- the operating system performance is simply too poor to support HDTV operation. The app takes almost 30 seconds to start or stop, 5 seconds to change channels.  
To be fair, I'm using VirtualBox, which probably cuts performance in half again. But on another box, an HVR-1250 PCI-E card running under 64-bit Oneiric manages only a hesitant, stuttering excuse for performance. Under Windows 7, the same hardware performs flawlessly. 

I'm curious as to whether other Linux distributions have more efficient code that might be up to the task. At least it only costs time to try!

---

### Post by inobe on 2011-10-29
hauppauge pvr performs flawlessly here, not even a hiccup, works the same on windows:p

---

