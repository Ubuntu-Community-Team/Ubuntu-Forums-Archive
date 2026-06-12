---
title: "How can I unmount a walkman without crashing"
date: 2014-09-23
forum: Multimedia Software
---

### Post by slowjoe2 on 2014-09-23
I'm using Philip Langdale's gvfs-mtp extension to interface with a Sony NWZ-B137F walkman.  Clementine can mount and read from the device, but I cannot figure out how to remove the device without crashing it.  Clementine sometimes crashes too.  I have to restart the computer before they will communicate again.  The system is 64 bit Xubuntu 12.04 with Thunar.

- *gvfs-mount -l* shows device seems to be mounted properly.
- using *gvfs-mount -u* then shows device is no longer mounted, however, the device still says it's communicating.  When I remove it, the device freezes and needs a hard reset.
- Clementine's 'safely remove device' option does not work to unmount it.
- Clementine can always recognise the device is plugged in.
- Once I've removed the device, I have to restart the computer, or the device will freeze again when it's reinserted.

Perhaps there's a set of mtp commands I should be using?

Kind thanks.

---

