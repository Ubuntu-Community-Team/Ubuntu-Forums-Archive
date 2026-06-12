---
title: "No sound nVidia 9800 GT 9.04"
date: 2009-11-29
forum: Multimedia Software
---

### Post by binabik80 on 2009-11-29
I have an Ubuntu 9.04 installation that works great.  I recently bought a new TV that I am hooking up to my second Video Channel of my 9800 GT to watch movies using a DVI - HDMI Cable (Audio is provide via a 3.5mm to L/R audio) which is how this TV works.
 
Here's my issue:
 
When using a similar setup in Windows XP I get audio and video fine on the new TV.
When using my Ubuntu Workstation I get video, but no audio. Cables are the same and I have tried many different cables.  
 
I am guessing here, but I am thinking that for some reason the HDMI input on the TV is overriding the L/R audio when connecting via Ubuntu.  Is there a setting in xorg.conf that would tell the TV not to expect audio?  
 
Any thoughts would be appreciated.

---

### Post by binabik80 on 2009-11-30
Fixed the issue.   

My issue was caused by the SPDIF being muted.

I installed the gnome-alsamixer and was able to unmute it.  Using the standard alsamixer the SPDIF was not selectable.  I am now happy to report that I have audio over my HDMI cable.

---

