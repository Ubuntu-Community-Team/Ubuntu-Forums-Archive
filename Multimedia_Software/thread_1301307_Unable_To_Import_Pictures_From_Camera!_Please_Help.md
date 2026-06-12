---
title: "Unable To Import Pictures From Camera! Please Help!!!"
date: 2009-10-25
forum: Multimedia Software
---

### Post by sting547 on 2009-10-25
Hi, I have recently upgraded to Ubuntu 9.04 and wanted to import the pictures from my Nikon Coolpix S210. When I try to open it in the file browser OR in F-Spot it says:

Error initializing camera: -60: Could not lock the device

Please Help!!!:(

---

### Post by fiver22 on 2009-10-26
I'm getting the same error message when trying to import from my Kodak DX4530. I can add that I haven't had any trouble with some other cameras on 9.04. In this case my camera shows up in f-spot but doesn't seem to mount (it doesn't show up under Computer or on Desktop). 
If it *does* mount for you I have read that in some cases UNmounting it and *then* trying to import with f-spot will work.

---

### Post by sting547 on 2009-10-26
I tried doing the unmount thing, but it still did not work. Do you think upgrading to Ubuntu 9.10 will help?:confused:

---

### Post by Sealbhach on 2009-10-26
Try booting up the computer with the camera attached, this used to make a difference with my modem at one time. Also enter the command:
```

lsusb

```
in a terminal when you have the camera attached, and copy and paste the output of it here.

.

---

### Post by HappyFeet on 2009-10-26
Try gthumb to import the photos.

---

### Post by oldfred on 2009-10-27
Years ago in windows I found it easier to pop the memory card out and use a usb card reader. I still do that in Ubuntu as I prefer manually copying to my own directory structure which I find easier to backup and then let picasa find the photos.

---

### Post by sting547 on 2009-11-04
I just upgraded to Ubuntu 9.10 and it fixed everything. Thanks though:D

---

### Post by The Oldun on 2009-12-04
> **sting547 said:**
> I just upgraded to Ubuntu 9.10 and it fixed everything. Thanks though:D
  I have tried using gthumb, I can see the thumbnails from the camera but it is not importing any where even select all import etc. I do not want to use F spot Karmic  any ideas?

---

