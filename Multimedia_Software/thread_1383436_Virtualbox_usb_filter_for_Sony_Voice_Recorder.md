---
title: "Virtualbox usb filter for Sony Voice Recorder"
date: 2010-01-17
forum: Multimedia Software
---

### Post by @tticus on 2010-01-17
Hi all, 

    I have a Sony ICD-P520 voice recorder. Since I have not found any alternative driver for ubuntu karmic I have installed the windows driver and program on a virtual machine. However I can not get my guest OS see the sony device. I have installed USBDevice to see all available devices in XP but it does not show any. 
I have created an usb filter for the device in virtualbox. Ubuntu can see it but XP does not. 
Could you please help me out ?

Thank,
   @tticus

---

### Post by @tticus on 2010-01-23
Any idea on how to solve this ?

---

### Post by bpalone on 2010-01-23
Which VirtualBox edition are you using?  The Open Source version does not support USB.  The PUEL version downloaded from [here]("http://www.virtualbox.org/wiki/Downloads") does support USB.  I think that I remember seeing somewhere that the newer versions of Ubuntu didn't need tweaking to get the USB to work the PUEL version of VirtualBox.  I could be wrong, have been in the past.

Good luck.

---

