---
title: "MKV playback corruption - Internal player"
date: 2011-09-28
forum: Mythbuntu
---

### Post by shad0w_walker on 2011-09-28
Ok. I've been trying to figure this one out all day and so far, no luck.

I have various MKV files which suffer from serious corruption when being played with the mythtv internal player. The image will start fine, then begin to corrupt into large blocks which hang from previous frames. Every so often it will hit a keyframe or enough of the scene will change to give me a clear image again.

I'm setup to use VDPAU for video decoding, currently using a 9600GT and before that (Swapped earlier today to rule out card)an 8600GT. Running latest Nvidia drivers from the site. The issue remains if I disabled VDPAU in playback settings.

The issue only occurs in the internal player as far as I can tell. I have played back the files on other machines with various programs and it never occurs, I have also played them back on the system using VLC and the video plays fine there.

Any ideas/help/fixes would be appreciated.

Running Mythbuntu 11.04 - Fulling updated (As of about 12 hours ago)

---

### Post by nickrout on 2011-09-29
what version of mythtv, and are you using mythbuntu repos?

what are the dimensions of the videos that fail?

---

### Post by shad0w_walker on 2011-09-29
Using all the standard mythtv repos, version .24/fixes

The video I've been using to test (Gives reliable corruption every time) has dimensions 700x480. H264 codec, 30FPS.
A couple of others that play with corruption: 1280x720, H264, 24FPS

Thanks for any suggestions you can give.

---

### Post by nickrout on 2011-09-29
> **shad0w_walker said:**
> Using all the standard mythtv repos, version .24/fixes

The video I've been using to test (Gives reliable corruption every time) has dimensions 700x480. H264 codec, 30FPS.
A couple of others that play with corruption: 1280x720, H264, 24FPS

Thanks for any suggestions you can give.

The reason I asked is that some video frame sizes give problems with vdpau on some chipsets, the readme that comes with your drivers explains.

---

