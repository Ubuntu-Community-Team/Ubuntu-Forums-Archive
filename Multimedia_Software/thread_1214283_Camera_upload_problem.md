---
title: "Camera upload problem"
date: 2009-07-15
forum: Multimedia Software
---

### Post by Brian Carruthers on 2009-07-15
I get the following error message when trying to upload *.jpg from my camera through a USB cable.

UNABLE TO MOUNT CANON, INC. Canon Digital Camera
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

Anyone had this experience?  My camera worked fine with Hardy.

Thanks.

---

### Post by aceole on 2009-07-15
Try a manual mount!

 Ubuntu Starter Guide, as follows:


   1. Created a new mount point: $ sudo mkdir /mnt/camera
   2. Mounted the camera: $ sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000

What do you mean, worked fine with hardy? did you change and to what?

---

### Post by Brian Carruthers on 2009-07-15
I updated my computer recently from 8.04 (Hardy Heron), and after that I couldn't load pictures. I am now working with release (9.04 Jaunty). 

I  tried your suggestion of a manual mount, and was able to retrieve images,
but the images were loaded automatically into Eye of GNOME Image Viewer previously.

Now the image viewer has an error message:

No images found in 'file:///home/brian/.gvfs/gphoto2 mount on usb%3A001,009'.

---

