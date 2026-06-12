---
title: "My video players work fine under gnome fallback, not Unity"
date: 2012-09-25
forum: Multimedia Software
---

### Post by Rob Sayer on 2012-09-25
What gives here?  My favorite video player (smplayer) doesn't work properly under unity but works the way it's supposed to under gnome classic/fallback.  Not under gnome 3.0 btw.

VLC works better under gnome fallback as well, but to a lesser extent.

Do these gnome/unity people just decide at some point their codecs are getting old and replace them?  It's not an improvement.

I like unity other than this (and the fact that dual monitor support is even worse with unity than gnome).  I understand the beta ubuntu update out now is supposed to deal mostly with unity ... is this being addressed?

---

### Post by BicyclerBoy on 2012-09-25
Depending on how you got VLC & mplayer changes whether they have completely self-contained codecs..

The std distro packages use the shared dynamically loaded system libraries.
The unity/gnome desktop devs people have nothing to do with codecs.

Your issues sound like video presentation..
What is your video h/w & driver ?

Unity uses composite manager compiz.
The composite effects manager works by re-direction of the screen redraw (same in MS windows).

You can try:
- full screen video
- use ccsm set un-redirect full screen
- try set "sync to vertical blank" in video driver settings.
- disable composite (no effects)
- try diff video output methods (Xv, opengl, vdpau, vaapi)

If you read phoronix benchmarking posts you see that:
- Unity/compiz has had performance problems from the start.
- KDE (with full bling/eye candy) is faster..
- seems to be a "blame game" between unity/compiz/video-driver..

---

### Post by Rob Sayer on 2012-09-27
> **BicyclerBoy said:**
> Depending on how you got VLC & mplayer changes whether they have completely self-contained codecs..

The std distro packages use the shared dynamically loaded system libraries.
The unity/gnome desktop devs people have nothing to do with codecs.

Your issues sound like video presentation..
What is your video h/w & driver ?

Unity uses composite manager compiz.
The composite effects manager works by re-direction of the screen redraw (same in MS windows).

You can try:
- full screen video
- use ccsm set un-redirect full screen
- try set "sync to vertical blank" in video driver settings.
- disable composite (no effects)
- try diff video output methods (Xv, opengl, vdpau, vaapi)

If you read phoronix benchmarking posts you see that:
- Unity/compiz has had performance problems from the start.
- KDE (with full bling/eye candy) is faster..
- seems to be a "blame game" between unity/compiz/video-driver..

Thanks for the response.

---

### Post by Rob Sayer on 2012-10-09
Installed ccsm (with some trepidation, I don't like those sort of utilities).

Tried set un-redirect full screen.  That seems to have done the trick.

Thanks, and also for the phorinix stuff.  Good site.

---

