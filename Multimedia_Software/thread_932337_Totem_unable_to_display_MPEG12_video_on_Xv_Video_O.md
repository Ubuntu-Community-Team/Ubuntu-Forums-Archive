---
title: "Totem unable to display MPEG1/2 video on Xv Video Overlay Device"
date: 2008-09-28
forum: Multimedia Software
---

### Post by Master One on 2008-09-28
A very strange problem. The video driver for my SiS Mirage*1 onboard graphics supports Xv modes "Overlay" and "Blitter".

No display problems with "Blitter", except that it does not support video resizing, making it totally unusable.

With "Overlay" Totem displays most video files without problems, except MPEG1 and MPEG2 videos, which are shown completely messed up (just some colors and patterns). When using VLC, everything is fine, which makes me assume, that it has something to do with the gstreamer configuration, or the codec used by gstreamer for MPEG1/2 video decoding.

I already searched the net all day, but nothing useful came up. Totem does not show any error messages in a terminal, if started with the debug option.

How is it possible, that Totem can show AVIs and MKV files (xvid, VC-1, whatever codec) just fine, but no MPEG1/2 files, when using the Xv Video Overlay device?

Anything else, that can be configured concerning gstreamer plugins / codecs, except "gstreamer-properties"?

---

