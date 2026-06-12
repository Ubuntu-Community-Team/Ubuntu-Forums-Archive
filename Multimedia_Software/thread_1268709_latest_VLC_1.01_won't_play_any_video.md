---
title: "latest VLC 1.01 won't play any video"
date: 2009-09-17
forum: Multimedia Software
---

### Post by bsmith1051 on 2009-09-17
I'm running 9.04 with an ATI 2100 videocard and the previous VLC 0.9.9 worked fine, aside from some minor GUI bugs.  I successfully upgraded another system to VLC 1.01 (from the PPA recommended on the Videolan.org web-site) so I did the same on this system.  Now, VLC crashes anytime I play a video?

I'm guessing it's yet another 'bug' with the unsupported ATI videocard.  My model seems to be the ONE model that is both too new to be supported by the open-source driver and too old to be supported by the ATI proprietary.

Any suggestions on how to troubleshoot this?  Worst case, of course, is to fallback to the old VLC.  I'm hoping there's some advanced video setting that will fix whatever is causing the crash...

P.S.  I'd also LOVE to update the video driver but I've given-up on that?

---

### Post by mc4man on 2009-09-17
If you used the korn ppa the open synaptic, search vlc and remove libvlccore[COLOR="Red"]0[/COLOR]

Then try opening vlc with this and see if any better (if you needed any config chages with 0.9.9 then you'll need to reset them in tools -> preferences
```
vlc --reset-config --reset-plugins-cache
```

Otherwise maybe search vlc, do a complete removal of all vlc packages, go into home folder and delete the vlc folders in .local/share ; .config ; .cache and then re-install

also if using pulse make sure you install the vlc-plugin-pulse

---

### Post by bsmith1051 on 2009-09-17
thanks for the suggestion re the pulseaudio plugin; I did not have that installed but when I added it, there was no change.

I have learned one additional thing, though.  Mplayer won't crash but it also won't playback with the default video renderer, xv.  If I switch it to X11, however, it works.  I tried the same thing in VLC but, again, it crashed.  I tried the null renderer and it worked (just audio and no crash) so clearly the issue is with the video renderer.

Again, I think I need to get a proper video driver....

---

### Post by bsmith1051 on 2009-09-18
Just went through the whole ATI-Video-Update-Why-Not research again.  The proprietary ATI Catalyst 9.3 driver _does_ support my card, but it only works on older versions of the X and X.org video-servers.  So as long as I'm running Ubuntu 9.04 (with X.org 1.6) I'm stuck...

---

### Post by scragar on 2009-09-18
Try changing the option that sets video to play in a seperate window to the interface, there was a bug at once point which caused VLC to crash if they shared a window.

---

### Post by mc4man on 2009-09-18
Haven't had an ati since a 9800pro on a p3, so don't know.

You could try using the OpenGl video output in vlc, won't hurt to try. ( Uses less buffers

---

### Post by bsmith1051 on 2009-09-18
> **scragar said:**
> Try changing the option that sets video to play in a seperate window to the interface, there was a bug at once point which caused VLC to crash if they shared a window.
That was it!  I disabled the option "Embed video in Interface" and it works again.  Thanks for your help!

---

