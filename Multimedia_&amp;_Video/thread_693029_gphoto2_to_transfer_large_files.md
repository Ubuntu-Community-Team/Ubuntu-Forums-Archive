---
title: "gphoto2 to transfer large files"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by mrgriscom on 2008-02-10
I am trying to transfer a 4GB movie file from my Canon digital camera to my Ubuntu laptop. The camera only supports the PTP protocol and cannot be mounted as a USB mass storage device.

As far as I can tell, gphoto2 (and the underlying libgphoto) tries to cache the entire file in memory before writing a single byte to disk. This seems like a pretty braindead design decision to me, and I don't know how to get around it. My computer only has 2GB of memory, and the process quits after allocating an additional ~1.3GB of swap (even though my total swap is larger than this).

Is there any setting that can make libgphoto work with a smaller cache and intermittently write out to a file as the transfer progresses? Or, is there any other option to get this file onto my computer (using PTP or otherwise)?

gphoto2 version is 2.3.1
libgphoto2 version is either 2.3.0 or 2.4.0 (I'm not quite sure which).

---

### Post by Tobi-fp on 2008-02-10
im really sorry about this, but im screwd.. How do you post a thread in here? i really need to know.. its so annoying.. I cannot figure it out :S hehe

---

