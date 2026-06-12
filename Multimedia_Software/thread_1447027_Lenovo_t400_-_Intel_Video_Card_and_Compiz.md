---
title: "Lenovo t400 - Intel Video Card and Compiz"
date: 2010-04-04
forum: Multimedia Software
---

### Post by zirtik on 2010-04-04
Hi,

I'm running Karmic Koala 64 bit on my Lenovo T400 laptop with switchable graphics having both Intel and ATI video cards. I've set my bios to use the intel card only and turned the automatic switching off. So far so good, but I'd like to turn on compiz for basic window animations. When I try to start compiz by selecting 

```
"Appearance Preferences" -> "Visual Effects" -> "Normal"
```

I get an error message saying "Desktop effects can not be enabled"

```
"System" -> "Administration" -> "Hardware Drivers"
```

doesn't show any new drivers that could be installed.

This was working  out of the box when I first installed Karmic Koala a few month ago, but things got messed up when I installed the restricted drivers for my ATI card. Now I can enable compiz if I switch to ATI from my bios settings and install the drivers but I don't want to use it due to high power consumption and I've removed the ATI drivers.

Here is my xorg.conf file:

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

It seems like my intel drivers are not even visible or installed. 

Thanks in advance.

---

### Post by zirtik on 2010-04-06
bump...

---

### Post by vancouverite on 2010-05-12
Hi zirtik,
I had the same problem and found that I needed to uninstall all the fglrx drivers, reconfigure the kernel, and remove the xorg.conf (it's not needed).

$ sudo apt-get remove --purge fglrx fglrx-amdcccle fglrx-modaliases
$ sudo dpkg-reconfigure linux-image-2.6.32-22-generic 
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bk

I don't know if the kernel reconfig is needed, but it's not harmful.  You may also be using a different version of the kernel, so after "linux-image", press tab and just go with the latest version, it's likely what you are using.

Van
Lucid 64bit

---

### Post by regiss on 2010-05-14
Hi guys, I have a T400 with ATI 3470 and Ubuntu 10.04 64bit. I can run flawlessly internal graphic car, but when I switch to my ATI then everything goes wrong. 
Resume is not working after suspend and approx. once a day it completely froze and only way how to resume is hard restart. 

I was using ati-driver-installer-10-4-x86.x86_64.run, however when I am using Internal graphic then everything works. 

Do you have any suggestion how to INSTALL ATI as I would like to use my ATI from time to time :)

Cheers regiss

---

### Post by David Vincent-Jones on 2010-05-15
t400 with 32 bit ....

If I install the"Ubuntu Certified" driver for the ATI Mobility Radeon 3470 the system becomes un-recoverable. Very nasty. I had similar problems on 9.04 and hoped that all had been solved by now.

Without the prescribed driver I am encountering freeze-ups pretty well every day that require a full hard power-off reboot.

Apparently I am missing all of the supposedly nice start-up features and at this time it looks like my OpenGL capability is crippled.

There must be somebody out there who has solved this problem ..

---

### Post by vancouverite on 2010-05-20
The ATI drivers have some issues.  Have you guys checked your memory usage during the day?  It may be that you have a memory leak or something.  There is a very active bug on Launchpad with info on the ATI card.  This is the second gen of this bug as the first one had 400+ posts!

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988)

Hope this helps!

Van

---

### Post by David Vincent-Jones on 2010-05-20
Thanks for the references.

This looks like a quite complicated issue with several extra items needed to be installed. Not what I would have expected from this current version of Ubuntu and I am quite surprised that the driver offered in the current package appears to have the blessing of the developers.

Hopefully I can find somebody who has a similar setup and can guide me through the changes ... these system crashes are not much fun through the recovery process.

---

