---
title: "Xubuntu Video Problem"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by Myomax65 on 2006-08-07
Video of any type presents with jumpy/bouncy playback. Effect is greatest when player's window size is small, but improves when at full screen. DMA is enabled on both hard drive and dvd-rom. Tried different players - mplayer, kaffeine, gxine - all the same. Help?

---

### Post by Ziox on 2006-08-07
> **Myomax65 said:**
> Video of any type presents with jumpy/bouncy playback. Effect is greatest when player's window size is small, but improves when at full screen. DMA is enabled on both hard drive and dvd-rom. Tried different players - mplayer, kaffeine, gxine - all the same. Help?

graphic card problem maybe? :( 

what's the output of this:

lspci -X | grep VGA

---

### Post by crumja on 2006-08-08
I recommend vlc for any video playing. It uses the least resources out of all the players out there, and has much more features.

For your specific problem, try posting the output of xvinfo.

If you're using an ati video card with fglrx, add Option TexturedVideo "On".

If not, use vlc and set the output module to OpenGL.

---

