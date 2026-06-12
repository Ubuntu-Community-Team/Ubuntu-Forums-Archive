---
title: "Hauppauge HD PVR won't mount to /dev/video*"
date: 2010-11-02
forum: Multimedia Software
---

### Post by kireol on 2010-11-02
I just purchased a HD PVR.  

It appears that I do not need extra drivers as they look to be in my kernel since ~2.6.29.1 [http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR) 

My box
```
uname -a
Linux brutus 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux
```

When I plug it in, it doesnt mount to /dev/video0

lsusb doesnt list the device.

dmesg reports the following:

```
[202390.400108] usb 1-3: new high speed USB device using ehci_hcd and address 82
[202405.520090] usb 1-3: device descriptor read/64, error -110
```

I tried googling and googling.  I tried a different USB cable.  I tried another ubuntu box.  

Could the device be bad or does it sound more like an option/driver issue?

Any help?

---

### Post by lidex on 2010-11-03
Familiar with this?
> Currently, firmware loading is unimplemented in the driver. As a result, if you have a "rev c1" unit you must install the HD-PVR at least once on a Windows machine to load the firmware into it. If you have a Revision 2 unit (including a sticker marked "rev c2" on the bottom of the unit) then it will come loaded with a firmware. Once you have done so, you will need a working build environment, Mercurial, and kernel headers installed on your system. In Debian and debian-based distros, the following command should install all necessary dependencies to build the driver. 

---

### Post by kireol on 2010-11-03
yup.  I am.  Mine is Rev E3.  So I don't think any of that applies to me.

---

