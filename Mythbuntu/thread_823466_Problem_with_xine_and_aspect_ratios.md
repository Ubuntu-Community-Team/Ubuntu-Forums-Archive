---
title: "Problem with xine and aspect ratios"
date: 2008-06-09
forum: Mythbuntu
---

### Post by the kaz on 2008-06-09
Hello all,
I have a small but annoying problem with my Mythbuntu 8.04 installation regarding the xine player that came with it. 

I have two displays that are both connected to the system via analog VGA - a 800x600 beamer and a 1366x768 TFT. Both must be connected via VGA as the beamer has no DVI/HDMI and the TFT doesn't use the native panel size unless connected via VGA. Thus, the VGA cable is connected alternativley to one of those two displays. 

That all is no problem; I even manages to configure X11 and the Nividia driver correctly so that both resolutions are supported. 
The system now always boots in 1366x768; I change the resolution manually to 800x600 when the beamer is used. This, however provides me with one problem: the xine player included in the distribution doesn't work correctly after I change the resolution from 1366x768 to 800x600. No matter what mode I chose, the picture always goes from Top zu bottom, even when it's a widedscreen recording, which should play letterboxed on a 800x600 4:3 screen.

VLC and mplayer both show the files correctly; I'd prefer the xine player, though, as that one seems to have the fastest H.264 (HD) decoding routines. Does anyone know what goes wrong here and how I can the xine that it's running on a 4:3 screen?

Greetings, the kaz.

---

