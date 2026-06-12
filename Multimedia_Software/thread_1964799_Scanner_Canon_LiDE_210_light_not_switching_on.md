---
title: "Scanner Canon LiDE 210 light not switching on"
date: 2012-04-24
forum: Multimedia Software
---

### Post by Jay Christnach on 2012-04-24
Ubuntu release 11.04.

The scanner is recognised, the scanning process seems to work (the scanning array assembly is moving), but the scan is dark, because the leds stay off.

I tried it inside a windows xp inside a virtual machine. And there the result was exactly the same.

I thought it could have to do with the usb drivers of the host pc, so I tried the scanner on my laptop. There it worked flawlessly. The laptop is also running 11.04.

I tried a new install of libsane with complete removal. No success.

sane-config --version gives 1.0.23
I discovered a symbolic link /usr/lib/sane/libsane-genesys.so.1 pointing to the shared object with version 1.0.22, so I changed this to point to 1.0.23. Now the scanner isn't recognized anymore.

The installed version of xsane is 1.0.22-2ubuntu1 according to synaptic.
So I changed the symlink back to what it was.

I remember I did some manual tinkering a few Ubuntu version before, because my scanner wasn't supported at that time and I got it to work, but I don't recall exactly what I did.

The version of the package is the same on the laptop. Also the two kernel versions are the same. 

Ok, since it didn't work in the Windows virtual machine on the desktop this is probably leading in a wrong direction. So maybe it has to do with libusb?
The versions of libub are also the same on both computers.

I tried to disconnect everything except the keyboard/mouse receiver and tried only with the scanner connected. No success. Also other usb devices work (printer sd-card reader, keyboard).

The cable I used on the laptop is the same than the one on the desktop, also it is known to work with my zoom h4 recorder.

What shall I try next? Thanks for any ideas!

---

### Post by zdeuyo on 2012-04-24
> **Jay Christnach said:**
> Ubuntu release 11.04.

The scanner is recognised, the scanning process seems to work (the scanning array assembly is moving), but the scan is dark, because the leds stay off.

I tried it inside a windows xp inside a virtual machine. And there the result was exactly the same.

I thought it could have to do with the usb drivers of the host pc, so I tried the scanner on my laptop. There it worked flawlessly. The laptop is also running 11.04.

I tried a new install of libsane with complete removal. No success.

sane-config --version gives 1.0.23
I discovered a symbolic link /usr/lib/sane/libsane-genesys.so.1 pointing to the shared object with version 1.0.22, so I changed this to point to 1.0.23. Now the scanner isn't recognized anymore.

The installed version of xsane is 1.0.22-2ubuntu1 according to synaptic.
So I changed the symlink back to what it was.

I remember I did some manual tinkering a few Ubuntu version before, because my scanner wasn't supported at that time and I got it to work, but I don't recall exactly what I did.

The version of the package is the same on the laptop. Also the two kernel versions are the same. 

Ok, since it didn't work in the Windows virtual machine on the desktop this is probably leading in a wrong direction. So maybe it has to do with libusb?
The versions of libub are also the same on both computers.

I tried to disconnect everything except the keyboard/mouse receiver and tried only with the scanner connected. No success. Also other usb devices work (printer sd-card reader, keyboard).

The cable I used on the laptop is the same than the one on the desktop, also it is known to work with my zoom h4 recorder.

What shall I try next? Thanks for any ideas!

Hello,

Honestly it seems to be a hardware failure. I have seen scanners when they get overpowered or hit by a power surge that this can cause the LED to fuz out.

Just to be sure, you can always install compatible software.

Here is a good article to check out:

Link: [http://www.bottomlesspit.org/2010/12/23/canon-lide-210-scanner-support-on-ubuntu-1010-maverick]("http://www.bottomlesspit.org/2010/12/23/canon-lide-210-scanner-support-on-ubuntu-1010-maverick")

Hope this helps.

---

### Post by Jay Christnach on 2012-04-24
Thanks for wanting to help zdeuyo!.

 But the scanner works without any problem on the laptop I mentioned which runs the (nearly or exactly?) same software.

It could be a power issue, because the scanner has no own power supply, so it draws its current from the USB port. That's why I tried disconnecting anything else. But I doubt that this is the case, because the stepper motor works and the led array (it's no tube) should not draw that much current.

I am pretty sure it is a software issue and if I have the occasion to test it somewhere else I'm also sure it will work on other computers. 

Best regards.

---

### Post by zdeuyo on 2012-04-24
> **Jay Christnach said:**
> Thanks for wanting to help zdeuyo!.

 But the scanner works without any problem on the laptop I mentioned which runs the (nearly or exactly?) same software.

It could be a power issue, because the scanner has no own power supply, so it draws its current from the USB port. That's why I tried disconnecting anything else. But I doubt that this is the case, because the stepper motor works and the led array (it's no tube) should not draw that much current.

I am pretty sure it is a software issue and if I have the occasion to test it somewhere else I'm also sure it will work on other computers. 

Best regards.

It was my pleasure to try and help.

The admins scan the forums so they may have an answer to this issue. Make sure to remain subscribed. Also, if you find a solution by all means post it in this thread.

All the best.

---

### Post by Jay Christnach on 2012-07-08
I determined that it is indeed a hardware problem, the hubs on my desktop computer do not deliver enough power. Maybe it is also a bad design on the scanner side, the unit should maybe have more capacitance to buffer the power supply. Also also heard that some cables have too much series resistance. 

I discovered scans beginning good with the light on and then finishing black after a few lines, even when I disconnect other usb devices. On the laptop it works everytime though. 

So I'm going to get a powered hub and see if that helps. If I get to an electronics shop I'll get some connectors, so I can try to  monitor the voltage on the 5 V lines.

Greetings, Jay.

---

