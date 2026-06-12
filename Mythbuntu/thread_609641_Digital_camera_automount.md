---
title: "Digital camera automount"
date: 2007-11-11
forum: Mythbuntu
---

### Post by J0ris on 2007-11-11
I would like MythGallery to import pictures straight from my digital camera through a usb hook-up. Unfortunately, the camera doesn't automount in Mythbuntu as it does in the regular Ubuntu distro. It does automount usb sticks and external hdd through the usb. How can I remedy this?

Thanks for any help!

---

### Post by kevinatkins on 2007-11-11
Hi,

I'm not overly familiar with Mythbuntu, but I'm guessing that libgphoto isn't installed perhaps so the camera isn't being detected (or, more accurately, it is being detected but there's no application configured to do anything with it...)

Also, cameras generally have two modes of operation - either using Picture Transfer Protocol (PTP), for which libgphoto is required, or as USB mass storage devices, where the camera will just appear as an external storage device. If you can, see if you can change the USB mode of your camera and see if that makes a difference. Also check whether libgphoto and gthumb are installed.

---

### Post by J0ris on 2007-11-17
Hi kevinatkins,

I installed libgphoto and gthumb while I was at it and it worked beautifully. However, the idea is that (ideally) MythGallery would be able to do this and it doesn't look like MythGallery is configured to use libgphoto. Any way to get this working as well?

---

