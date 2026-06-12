---
title: "Major laggy MKV playback"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by lefty182 on 2008-04-04
This problem is very annoying. I've been trying to fix it for a few days. I can't get mkvs to play for the life of me.

I've tryed : 
Disabling beryl
reinstalling graph drivers
installing restricted codecs
installing mplayer,smplayer,xine,kaffeine, and so on.
installing vlc [this has codecs inside it and STILL lags]

My comps specs are as follows :
# AMD Sempron 3500+ (1.8GHz/512Kb)
# 15.4" Ultrasharp WXGA display
# 2GB DDR2 SDRAM
# ATI Xpress 1150 256MB HyperMemory (Integrated graphics)
# 60GB 5400RPM SATA Hard Drive
# 24x CD Burner/DVD Combo Drive
# 6-cell 53 WHr lithium-ion battery
# Microsoft Windows XP Media Center Edition
# Dell 1390 802.11g Mini Wireless Card

I've also tried changing from xm to xm11 and so on.

If anyone has any solution for this it would be greatly appreciated. 

PS - I think it has something to do with graph drivers even though linux says they're installed properly. The reason I think that is that vlc lags, which is very strange since it does have internal codes.

---

### Post by eye208 on 2008-04-04
> **lefty182 said:**
> # AMD Sempron 3500+ (1.8GHz/512Kb)
Semprons are too slow to decode high definition H.264 streams in realtime.

---

### Post by lefty182 on 2008-04-05
Sorry its 2ghz. Still thats strange though cuz I could play 1280x720 mkvs easily on windowsXP

---

### Post by Melcar on 2008-04-05
I don't think any of the proprietary drivers (nvidia or ATI) has proper support for HD content decoding, so all is done in the CPU, which in your case, may be too slow for the task.

---

