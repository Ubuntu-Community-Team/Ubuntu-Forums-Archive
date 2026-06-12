---
title: "Can't import from Canon digital camera"
date: 2013-06-24
forum: Multimedia Software
---

### Post by piotrl on 2013-06-24
> **thekennedy said:**
> Same problem with my XTi/400D, same "fix" worked for me.  I just chose another USB port, thanks for the pointer!

I have a new laptop, and I tried plugging in the camera to the three different USB ports, but none of them work.  Any ideas for other options if none of the ports work?
Thank you.

---

### Post by oldos2er on 2013-06-24
Post moved to its own thread.

---

### Post by tgalati4 on 2013-06-24
Look in the camera settings and set USB port to "Data Transfer" or "File Transfer" mode.  Some camera USB ports are used for multiple purposes, so you have to specify how you want to use it within the camera.

---

### Post by oldfred on 2013-06-25
With all my cameras I extract card and use a USB card reader. I got mine many years ago for about $10 and it was a 7 in 1. New ones are like 25 in 1 and half the cost.

---

### Post by piotrl on 2013-06-25
Thank you.  I do have a reader and it does not read that either.  The reader and camera is fine with my old pc that shows the older usb version.  Any other ideas?
Thank you.

---

### Post by tgalati4 on 2013-06-25
Is this a USB3 port?  Perhaps you can set USB2 compatibility mode in the BIOS.  What computer and camera model?

---

### Post by piotrl on 2013-06-26
It's a Dell Insprion 15R, 8GB RAM, 1TB hard drive, 4X Intel Core i5-3337U 1.8 GHZ
The camera is a Canon EOS Kiss X or Rebel XTI.

This is what I get with lsusb on the new pc.  The old one has 2.0, 1.1, 1.1, 1.1, 1.1.

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 

I'm not fluent or even partially knowledgable in using code in Terminal.  I do copy and paste different codes, but don't know the details of how it all works.  This means that if you can give me the steps to update in Bios that would be appreciated.
Bus 001 Device 005: ID 0c45:64ad Microdia

---

### Post by piotrl on 2013-06-28
There was nothing in BIOS for settings.  An IT guy I know said that it might be a 64-bit issue in that the card reader and camera does not want to communicate with.  I bought a USB 3.0 card reader, and that works.
Thank you all for helping.

---

