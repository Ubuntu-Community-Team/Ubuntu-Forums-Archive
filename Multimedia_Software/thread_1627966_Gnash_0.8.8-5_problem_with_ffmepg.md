---
title: "Gnash 0.8.8-5 problem with ffmepg"
date: 2010-11-22
forum: Multimedia Software
---

### Post by Farinet on 2010-11-22
Recently i installed the new Gnash 0.8.8-5 (i got it from a debian squeeze package). For installation it required removing of several files (in lib i presume):
#
libavdevice-extra-52 (multiverse)
#
libavformat-extra-52 (multiverse)
#
libavutil-extra-49 (multiverse)
#
libpostproc-extra-51 (multiverse)
#
libswscale-extra-0 (multiverse)

plus: gstreamerffmpeg (and several players like VLC e.g.)

The files above were substituted by equally named files without the <extra> in the name. Now, the problem is, i can see pretty well Youtube in FF, yes, the improvement over 0.8.7 which came with 10.04 and is in the related repositories is impressive!, but: no mediaplayer is working anymore. When i try to reinstall ffmpeg it always requires to delete gnash. And that's always the same regardless i'm installing from the ubuntu repositories, from debian or directly from the ffmpeg site.

Does anyone have an idea.

Oh, i'm using Lucid on a PB G4 and i posted here because it seems to me something software related not hardware. 

TIA

---

