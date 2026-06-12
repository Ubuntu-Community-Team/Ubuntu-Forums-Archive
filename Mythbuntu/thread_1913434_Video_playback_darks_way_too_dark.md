---
title: "Video playback: darks way too dark"
date: 2012-01-22
forum: Mythbuntu
---

### Post by ErWenn on 2012-01-22
I'm running Mythbuntu 11.10, using an old NVIDIA GeForce FX 5200 video card, outputting through DVI (via a DVI-to-HDMI cable) to a brand new 40" Element edge-LED-backlit LCD TV at 1080p. Whenever I play back a video, dark scenes come out way too dark. The bright colors look fine, but I can barely make out any detail at all in the dark parts of the screen. I've been unable to mitigate this by messing with the brightness, contrast, or other settings on my TV (switching from "home" to "standard" mode doesn't help either). I also messed around with the color settings in the "NVIDIA X Server Settings" to no useful help. I get the same troubles when I use VLC player or mplayer.

(I've got a newer (VDPAU-capable) video card in the mail, but I have no idea if that will fix the problem.)

Any thoughts on how to fix this?

---

### Post by nickrout on 2012-01-22
> **ErWenn said:**
> I'm running Mythbuntu 11.10, using an old NVIDIA GeForce FX 5200 video card, outputting through DVI (via a DVI-to-HDMI cable) to a brand new 40" Element edge-LED-backlit LCD TV at 1080p. Whenever I play back a video, dark scenes come out way too dark. The bright colors look fine, but I can barely make out any detail at all in the dark parts of the screen. I've been unable to mitigate this by messing with the brightness, contrast, or other settings on my TV (switching from "home" to "standard" mode doesn't help either). I also messed around with the color settings in the "NVIDIA X Server Settings" to no useful help. I get the same troubles when I use VLC player or mplayer.

(I've got a newer (VDPAU-capable) video card in the mail, but I have no idea if that will fix the problem.)

Any thoughts on how to fix this?

Do thise happen to be xvid files at a low bitrate? Blacks and near blacks are notoriously badly encoded in such situations.

---

### Post by ErWenn on 2012-01-22
Most of my videos are. My poor little box can't really handle 720p or bigger (the main reason for the new video card on the way). But I did a cursory check on some better resolution files and the problem was still there. I'll double check on that.

---

