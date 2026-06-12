---
title: "mpd alsa alongside pulseaudio"
date: 2012-03-16
forum: Multimedia Software
---

### Post by Jeek Elemental on 2012-03-16
Would like to have mpd "own" the optical out with no interference (its only used for music) while pulseaudio uses hdmi sound for everything else.

Can I just set mpd to alsa output or will pulseaudio try to grab it?

---

### Post by prupert on 2012-07-22
Did you get anywhere with this?

I am looking to use alsa to access the optical out for bitstreaming and then use pulse to stream using rtp to other devices....

---

### Post by Jeek Elemental on 2012-07-25
Yes it works nicely, mpd uses optical out while xbmc/everything else use hdmi audio.
Optical is still there as a pulse sink.

---

