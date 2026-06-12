---
title: "Choppy Graphics after Xorg Update"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by blissend on 2006-07-14
With the latest nvidia-glx, my card (geforce 6600) worked fine until Ubuntu wanted to update the xorg thing. Afterwards, I noticed the screensavers that utilize 3d stuff became very choppy. Is there anyway to fix that? Any help would be appreciated.

NOTE: I don't have xgl

---

### Post by blissend on 2006-07-16
Correction, all screensaver stuff is choppy. I hope this doesn't affect my gaming... I'll have to test that. This is the reason I bring this topic up. I couldn't care less about screensavers, just gaming). Also, my sound and vids are fine unless they're 3d.

---

### Post by tseliot on 2006-07-16
Try reinstalling the Nvidia driver:
```
sudo apt-get install --reinstall nvidia-glx linux-restricted-modules-`uname -r` nvidia-kernel-common
```

OR (IF YOU USE LEGACY DRIVERS)
```
sudo apt-get install --reinstall nvidia-glx-legacy linux-restricted-modules-`uname -r`
```

---

### Post by futz on 2006-07-16
> **blissend said:**
> With the latest nvidia-glx, my card (geforce 6600) worked fine until Ubuntu wanted to update the xorg thing. Afterwards, I noticed the screensavers that utilize 3d stuff became very choppy. Is there anyway to fix that?
Ummm... How did you "update the xorg thing"??? I ask this because when you use "sudo dpkg-reconfigure xserver-xorg", and let it automatically find your video hardware, it finds and defaults to the "nv" driver. You have to manually move the selector down one to "nvidia" so it uses the glx driver.

Do you see the Nvidia screen on bootup now? If not, then your 3D graphics *will* be slow, because you're not using the proper driver.

I could be wrong, but I just went thru all this yesterday. Finished changing things around to suit a new LCD monitor and suddenly Google Earth complains about no or bad driver and won't work at all. I reran "sudo dpkg-reconfigure xserver-xorg" and selected nvidia instead of nv and all was working again.

---

### Post by tseliot on 2006-07-16
> **futz said:**
> Ummm... How did you "update the xorg thing"???
I think he refers to the update of xserver-core from ubuntu's updates

---

### Post by blissend on 2006-07-17
Thanks for the replies. :D

I was refering to the Ubuntu updates for xorg-core. Should have been more specific, my bad. The command...

```
sudo apt-get install --reinstall nvidia-glx linux-restricted-modules-`uname -r` nvidia-kernel-common
```

worked for me. I thought I updated nvidia through snyaptic but didn't realize there was more to it than just nvidia-glx. Thanks tseliot.

---

