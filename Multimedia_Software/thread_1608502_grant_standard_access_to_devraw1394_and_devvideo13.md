---
title: "grant standard access to /dev/raw1394 and /dev/video1394/0"
date: 2010-10-29
forum: Multimedia Software
---

### Post by jdesonneville on 2010-10-29
Hi,

I've got a firewire camera (from the imaging source), and I use the coriander software package for viewing and recording etc.

Currently after rebooting the computer, I have to either use coriander as root, or change the owner of /dev/raw1394 and /dev/video1394/0 to the user, before I can use the camera.

I'd like other users also to make use of the camera, with an own login, and don't like to explain the setup or give root access to them.

Is there an way to setup the firewire port in ubuntu such that the logged-in user can access the firewire camera immediately?

Thanks for your help,
Jan

btw I currently use 10.10 64 bit ubuntu, but I have the same problem with different (32 bits) and previous versions as well.

---

