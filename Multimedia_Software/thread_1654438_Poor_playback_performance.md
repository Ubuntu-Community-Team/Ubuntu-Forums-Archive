---
title: "Poor playback performance"
date: 2010-12-28
forum: Multimedia Software
---

### Post by unauthorized on 2010-12-28
I'm trying to get a rather old box to play HD content under Ubuntu. The  box in question is a P4 1.8Gz 130nm CPU, 512MB RAM and a Radeon 9550.  Under a standard Windows XP + ATI driver installation, it's possible to  play 720p content with VLC nearly flawlessly.
However, performance  under Ubuntu is less than desirable. Trying to play the same 720p clip  with VLC or Totem results in very poor playback with less than 1 frame  per second. mplayer displays a smooth video output, but it progressively  lags behind the audio stream.

3D acceleration is enabled, all desktop effects are disabled and the wm is metacity.
I  tried using the new X350 drivers from xorg-edgers but the only notable  result was glxinfo segfaults.The legacy ATI binary driver doesn't  support any Xorg since 1.5 (ie Hardy) so that's out of the question as  well.

Any ideas?

---

### Post by VonSpyder on 2010-12-28
some possibilities:

Turn off compiz if its on, even if no desktop effects are eneabled.
Try another media player like Dragon.
Try a different distro like Xubuntu as it requires fewer system resources.
add RAM.

see if any of those do the trick.

---

### Post by unauthorized on 2010-12-28
> **VonSpyder said:**
> some possibilities:

Turn off compiz if its on, even if no desktop effects are eneabled.
Try another media player like Dragon.
Try a different distro like Xubuntu as it requires fewer system resources.
add RAM.

see if any of those do the trick.
I'm using metacity so obviously compiz cannot be running. My comment was about gnome's desktop effects.
I  can't even get dragon to play restricted formats, but I've tried  several players with different back ends, so it's safe to  assume that the problem is related to one or two specific players/backends.
XUbuntu isn't any faster than the regular Ubuntu and RAM isn't really a  problem in this case. I'll test playback under XFCE anyway but I have my doubts about it.

---

