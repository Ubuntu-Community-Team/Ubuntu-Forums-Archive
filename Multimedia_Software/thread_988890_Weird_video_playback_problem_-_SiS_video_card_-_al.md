---
title: "Weird video playback problem - SiS video card - all players affected"
date: 2008-11-21
forum: Multimedia Software
---

### Post by EvilCouch on 2008-11-21
**Work-around found**
Changing VLC video preferences to use "X11 video output" allows video to work properly under VLC.
****

I recently migrated to Ubuntu 8.10 from Debian and have ran into a weird problem with playing movie files.

If I try to play anything, in any player, I get extremely distorted video. It looks like the top row of pixels get drawn all the way down (i.e. all I get is a lot of appropriately colored and vertical stripes). There are no errors reported in VLC if I open it in console mode.

However, if I open the same file in a second instance of the player, the second instance works relatively normally. I say relatively because while it gives me proper playback, the video itself will not stretch to fit the window, nor can it be zoomed in or out by any method. (i.e. the actual size of the video output stays the same, regardless of what the player is telling it to do.)

> lspci | grep Display
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)


****
Work-around found as I was typing this up. Submitting it anyways because the root cause is still there and the work-around might help someone else.

---

