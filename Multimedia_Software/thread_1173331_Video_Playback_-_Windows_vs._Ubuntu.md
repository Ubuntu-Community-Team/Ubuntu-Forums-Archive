---
title: "Video Playback - Windows vs. Ubuntu"
date: 2009-05-29
forum: Multimedia Software
---

### Post by Shibblet on 2009-05-29
I am noticing some playback issues with Totem in Ubuntu 9.04.  It looks as if the playback isn't as fast as it is in Windows XP.

Is this an OS issue, or does it have more to do with the player?

---

### Post by Shibblet on 2009-06-01
Bump.

---

### Post by Arup on 2009-06-01
Have you installed the video drivers? Movies with mplayer and vdpau enabled on my nvidia card run fine, HD mode in full screen as well.

---

### Post by Shibblet on 2009-06-03
> **Arup said:**
> Have you installed the video drivers? Movies with mplayer and vdpau enabled on my nvidia card run fine, HD mode in full screen as well.

Yes, latest-greatest nVidia drivers.  It looks like a frame rate or refresh issue.

---

### Post by Arup on 2009-06-03
> **Shibblet said:**
> Yes, latest-greatest nVidia drivers.  It looks like a frame rate or refresh issue.

Instead of totem install mplayer and gmplayer and enable vdpau by following instructions here at [https://launchpad.net/~brandonsnider/+archive/ppa](https://launchpad.net/~brandonsnider/+archive/ppa)

vdpau will give you the frame rates you are looking for as it will unload the decoding to the powerful GPU of the nvidia card.

---

