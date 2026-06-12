---
title: "Ubuntu Edgy/6.10 Kino and *1394/firewire drivers"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by scarpent on 2007-05-26
I've been beating my head against the IEEE1394 wall for a while now, and have found many helpful tips here and otherwise, but so far no luck.

Here's what I have: A Panasonic camcorder and a 1394/Firewire PCI card.  The card and the cable worked ok on my Windows machine.  I'm pretty sure I have an NVidia graphics card (came with my system76 machine).

I usually can run **sudo modprobe raw1394** and get ls -l:

crw-rw---- 1 root disk 171, 0 2007-05-26 22:21 raw1394

Sometimes **sudo modprobe dv1394** works for creating the necessary /dev entry, or sometimes I've tried **sudo mknod -m 666 /dev/dv1394/0 c 171 32**.  (I'll worry about better permissions later after I get it working.)

Tonight as I write this I had to use the mknod command.

In /dev/dv1394:

crw-rw-rw- 1 root root 171, 32 2007-05-26 22:26 0

Now I start Kino (0.9.0) with **gksudo kino &**.

Preferences --> IEEE1394, dv1394 device = /dev/dv1394/0

Camera is on.  I click on "Capture", and get this message in the status bar at the bottom of Kino:

WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!

And all of the camera control buttons in Kino are disabled.

I've tried many, many configurations with various permissions and groups assigned.  I've tried playing around with video1394 instead of dv1394.

Any ideas?  I'm really spinning my wheels here.

*Thanks!*

Some other places I've looked:

[http://ubuntuforums.org/archive/index.php/t-2792.html](http://ubuntuforums.org/archive/index.php/t-2792.html)
[https://launchpad.net/ubuntu/+source/kino/+bug/6290](https://launchpad.net/ubuntu/+source/kino/+bug/6290)
[http://tonywhitmore.co.uk/blog/2006/11/08/ubuntu-edgy-and-dv-cameras/](http://tonywhitmore.co.uk/blog/2006/11/08/ubuntu-edgy-and-dv-cameras/)

Helpful information, and maybe my answer is there or in the other places I've found, but I haven't been able to connect the dots.

---

### Post by scarpent on 2007-05-28
Well I gave up on the machine I was working on and tried on another machine by booting with a Live Ubuntu Feisty/7.04 CD. (This is the same Windows machine I had previously had the card in.)

Installed Kino which gave me 0.9.2 this time. I saw that dv1394 and raw1394 were automatically set up now.

And... Capture works great!

---

