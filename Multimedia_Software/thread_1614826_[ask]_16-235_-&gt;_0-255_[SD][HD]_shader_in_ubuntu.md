---
title: "[ask]: 16-235 -&gt; 0-255 [SD][HD] shader in ubuntu?"
date: 2010-11-06
forum: Multimedia Software
---

### Post by chrone on 2010-11-06
is there a movie player with 16-235 -> 0-255 [SD][HD] shader in ubuntu?

i've tried VLC and Gnome Movie Player but they didn't have the option to use that shader. the color of the video looks so washed out without the shader.

in windows i used to use Media Player Classic Home Cinema, installed from K-Lite Mega Codec.

---

### Post by SoulSmasher on 2011-02-04
Anyone has a solution for this ? it would be appreciated. Thanks!

---

### Post by BicyclerBoy on 2011-02-05
If I understand you.. want to make the video playback in the right colour-space.
SD HD have diff colour-space.
PC & video RGB have diff colour-space.

For nvidia GPU h/w decode..
vdpau playback allows manual &/or auto-correct colour space.

see vdpau filters: vpdaustudio, vdpaucolorspace=n. 
n=0: will use BT709 for HD videos and BT601 for SD 
n=1 (default): will always use BT601 
n=2: will always use BT709 
also check out vdpau: sharpen denoise hqscale.

MythTV XBMC has full support for these filters.
mplayer has cmd-line options for these.

VLC has sub-optimal video playback control even with va-api.

If you have HDMI interconnect then consider YCbCr instead of RGB encoding.

---

