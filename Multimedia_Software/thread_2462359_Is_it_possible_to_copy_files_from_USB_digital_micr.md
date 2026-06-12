---
title: "Is it possible to copy files from USB digital microscope?"
date: 2021-05-19
forum: Multimedia Software
---

### Post by smith73 on 2021-05-19
I am planning to buy an USB digital microscope camera (rather cheap one though portable) 
and at main vendor's website the system requirements for it are generally varieties of Windows.
 I suppose there will be a CD with the drivers for Windows shipped also. Apart from using the microscope
 only on Windows virtual machine, can it be expected that the microscope would also connect to Ubuntu
 normally via USB (at least for copying images from the camera)?

For example, I didn't install KDE Connect Indicator app on PC Ubuntu 20.04 distro, but have a similar app installed
on an Android phone. Yet after connecting an Android phone via USB Ubuntu opened the folder with Android 
files normally for copying. Can it be supposed that the same would happen upon connecting a microscope camera via USB?
Or should I search for additional microscope drivers for Linux? Or search for USB microscope cameras explicitly supporting Linux?

---

### Post by The Cog on 2021-05-19
If it's a cheap microscope, I would guess it uses a cheap/commodity webcam sensor. My guess is that you have a reasonably good chance of it working out of the box, and be able to see the images with a webcam app like cheese. But I am only guessing. Other opinions may be much better informed than I am. It is certainly worth searching for ones that explicitly support Linux, to remove doubt.

---

### Post by TheFu on 2021-05-19
A friend has a $30 cheapo "microscope" like this.  It appears as a webcam in Linux, so **cheese** and **guvcview** and **obs** or any other Video4Linux2 software can be used.

The key question is whether Video4Linux2 supports the device or not.  I'd use **lsusb**, get the USB identifier and look at whether that is supported on Linux or not by drivers included in the kernel.

---

