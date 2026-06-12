---
title: "Can't capture Video"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by jmtjet on 2006-12-15
How can I tell if my ieee1394 firewire PCI card has a driver installed? Kino opens, but when I click "capture" nothing happens. If I need a driver, could someone recommend one to me? I really would like to get my video capture working in Ubuntu, that's the last hurdle for me. 
I'm trying to capture from a Sony Handicam using miniDV tape. Thanks.

---

### Post by Quicky on 2006-12-16
My advice is to install gscanbus from Synaptic, plug in and turn on your camcorder, then in a terminal run gscanbus. A little window should appear showing your connection to the camera if everything is okay.

FYI, I found this thread very helpful when setting up my DV capture:

[http://ubuntuforums.org/showthread.php?t=56468&highlight=raw1394](http://ubuntuforums.org/showthread.php?t=56468&highlight=raw1394)

---

### Post by jmtjet on 2006-12-16
Thanks for the reply and link. There's a lot of good info in the link. I'll be trying to capture tonight and will post back with my results. :)

---

### Post by jmtjet on 2006-12-16
OK, when I use the command; sudo Ismod | grep 1394. I get this:

dv1394                 21196  0
raw1394                30956  0
scsi_mod              139496  5 sr_mod,sbp2,sg,sd_mod,usb_storage
ohci1394               35124  1 dv1394
ieee1394              299832  4 dv1394,raw1394,sbp

Not sure if this means my 1394 card is loaded or not? Any ideas? Thanks.

---

### Post by vgrisham on 2006-12-24
> **Quicky said:**
> My advice is to install gscanbus from Synaptic, plug in and turn on your camcorder, then in a terminal run gscanbus. A little window should appear showing your connection to the camera if everything is okay.

FYI, I found this thread very helpful when setting up my DV capture:

[http://ubuntuforums.org/showthread.php?t=56468&highlight=raw1394](http://ubuntuforums.org/showthread.php?t=56468&highlight=raw1394)

Hi,

I too am trying to get my firewire camcorder working with Ubuntu. I ran gscanbus and it reported, "Couldn't get handle: No such file or directory
This probably means that you don't have raw1394 support in the kernel or that
you haven't loaded the raw1394 module."

What should I do next?

Thanks,
Vaughn

---

