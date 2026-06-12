---
title: "ATI X1300 - Diagonal 'tear' on video under MPlayer, VLC"
date: 2009-01-18
forum: Multimedia Software
---

### Post by badgerm on 2009-01-18
I've installed the ATI video driver for my Radeon X1300, but have a weird issue when playing video through MPlayer, VLC and XBMC. When there is a lot going on (shot changes, lots of movement, etc.) the video seems to tear diagonally from the top left to bottom right of the display. It looks as though the display is in two halves, but is only noticeable at the join. The effect is uniform across all video formats, including DVDs, and only affects the video itself; if windowed the rest of the display is fine.

Does anyone have any ideas? I can't play DVDs without the prop. drivers installed, and can't image that my system is too slow (Athlon 64 3200, 1GB RAM). My first non-virtual foray into desktop Linux has caused me a few issues, but no others that I've not been able to resolve via searching online. It's driving me up the wall!

Cheers

---

### Post by listerthrawn on 2009-01-18
Hi,

Try turning off the desktop effects and see if you have the same issue (System-> Preferences-> Appearance and the visual effects tab).

---

### Post by badgerm on 2009-01-18
No change unfortunately, I turned off everything in Compiz too, to no avail.

---

### Post by theApokalypsis on 2009-01-18
Did you try using Non xV playback as a temporary workaround?

i.e.

Totem
- Alt-F2
- gstreamer-properties

change under video tab from autodetect to (No xV)

VLC I believe you can change in its preferences.

Jaunty is just around the corner with this issue being fixed :).

---

### Post by Melcar on 2009-01-18
All Linux drivers suffer from some from of tearing (how severe depends on the driver/system).  Radeon and radeonhd suffer from it, Intel drivers a little, and not sure for nvidia (I'm guessing not).  It has something to do with X and it's not just the driver's fault.  Using opengl instead of Xv and forcing vsync. on seems to fix it for some people.

---

### Post by badgerm on 2009-01-18
^
|
|

Cheers both, I'll have a play around and keep my fingers crossed for Jaunty.

---

