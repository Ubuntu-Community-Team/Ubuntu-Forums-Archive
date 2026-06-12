---
title: "Kino not recognizing my Firewire video recorder"
date: 2009-07-31
forum: Multimedia Software
---

### Post by mmcmonster on 2009-07-31
I have a Sony TRV27 camcorder that worked fine with Kino on Ubuntu about a year ago.

I am now running Ubuntu 8.04, and set my permissions on /dev/raw1394 appropriately:
```
$ ls -l raw1394 dv1394-0 
crw-rw-rw- 1 root root 171, 32 2009-07-31 12:05 dv1394-0
crw-rw-rw- 1 root root 171,  0 2009-07-31 12:05 raw1394

```When I initially attached the device to the computer, it automatically created /dev/raw1394.  When Kino didn't work, I then added /dev/dv1394-0 using modprobe.  Kino still doesn't work:

**When I run Kino with the video recorder attached, it doesn't give any error messages, but also doesn't allow me to use the device.  Even if I hit play on the device itself, Kino doesn't do anything.** :-(

The device appears to be recognized by Kino, however.  Under Edit->Preferences->IEEE1394 my camcorder is properly identified.

What am I missing?

---

### Post by mmcmonster on 2009-07-31
My bad.

I didn't realize that Kino doesn't default to the "Capture" tab on the right side of the screen when starting a new project.

Man, do I feel sheepish. :-)

---

