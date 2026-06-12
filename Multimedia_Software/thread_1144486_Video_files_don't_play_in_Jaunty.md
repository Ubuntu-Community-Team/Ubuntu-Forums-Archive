---
title: "Video files don't play in Jaunty"
date: 2009-04-30
forum: Multimedia Software
---

### Post by bodycoach2 on 2009-04-30
After upgrading to Jaunty, my video files don't play. They played fine on the same computer in Hardy and Intrepid, but I get 1/4 second, sound but no video, and the program closes. This happens with MPlayer, Totem, VLC, and SMPlayer. Youtube plays fine.

Any ideas?

---

### Post by primowalker on 2009-04-30
> **bodycoach2 said:**
> After upgrading to Jaunty, my video files don't play. They played fine on the same computer in Hardy and Intrepid, but I get 1/4 second, sound but no video, and the program closes. This happens with MPlayer, Totem, VLC, and SMPlayer. Youtube plays fine.

Any ideas?

--------
I'm seeing the same thing as well.  Here is the error I get when I try to play a video with totem from the cli:

**The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 76 error_code 11 request_code 132 minor_code 19)[/I]

And the same file with vlc:

[I][????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)[/I]

---

### Post by naja74 on 2009-06-13
Same here. I KNEW I shouldn't have upgraded!!  ::head-desk::

Hopefully a solution will be posted shortly. I would hate to have to do a clean install back to 8.10.

---

### Post by naja74 on 2009-06-18
My issue has been resolved by reverting the xorg intel driver to 2.4.

[[COLOR="Blue"]Instructions can be found here[/COLOR]]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

---

