---
title: "Unable to create LiveUSB with Maverick Netbook Edition ISO"
date: 2010-09-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2010-09-02
I've downloaded the netbook beta ISO and fired up USB creator on my fully updated maverick, I have formated the USB and selected it on the usb creator, and then I select the .iso but it won't show up, and I can't click the 'install'.. 

Any ideas??

---

### Post by bennachie on 2010-09-02
The most common problem would be a malformed ISO (which is therefore not recognised as a legitimate Ubuntu image). That could result from an error during the download process. Have you checked the md5sum?

Incidentally, if you do get things working, it may be necessary for you to disable persistence in order to have the USB stick operate properly. This is apparently a temporary workaround to a bug (627672) whose solution has been identified, but cannot be implemented in time for the Beta release.

---

### Post by VMC on 2010-09-02
> **lee.jarratt said:**
> I've downloaded the netbook beta ISO and fired up USB creator on my fully updated maverick, I have formated the USB and selected it on the usb creator, and then I select the .iso but it won't show up, and I can't click the 'install'.. 

Any ideas??I''m sure you know that the USB hard drive needs to be formated as fat.

edit: what doesn't show up, the iso or the usb?

---

### Post by go7Ul1ai on 2010-09-02
Thanks for your replies, someone helped me over on #omg!ubuntu! 

I installed zsync and downloaded directly like that.. I tried doing 2 standard downloads before this which failed, it was the md5 checksum which was the problem.

I can now mark this as solved! :)

---

