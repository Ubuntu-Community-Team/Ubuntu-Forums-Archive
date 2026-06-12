---
title: "SD-Card have to Reboot"
date: 2010-02-18
forum: Multimedia Software
---

### Post by Rodney9 on 2010-02-18
Hello, I have to reboot every time I put a different sd card in.
After I take the first one out the built in reader in my Dell monitor sdf1 still has those first photos in it no matter how many other cards I put in.

How do I fix this ?

---

### Post by efflandt on 2010-02-18
Have you tried right clicking that device and Eject or Unmount (or **sudo umount**  the mount point for that device in a terminal)?  Otherwise Linux may be caching old data and does not know that you changed the media.

In days past all devices had to be mounted or umounted manually.  With automounting, USB will recognize when a USB device is disconnected, but may not realize that storage media has changed in a device, if the reader device itself has not been disconnected.

---

