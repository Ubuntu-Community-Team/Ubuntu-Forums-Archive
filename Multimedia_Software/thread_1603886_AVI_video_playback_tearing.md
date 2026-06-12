---
title: "AVI video playback tearing"
date: 2010-10-23
forum: Multimedia Software
---

### Post by Linux_FTW on 2010-10-23
Hey guys,

I'm sorry if this was asked before (i know it was but never worked for me)

2 days ago I installed ubuntu 10.10, my very first linux OS and I immediately fell in love with it.

The only problem now, is tearing during video playback
(I'm a perfectionist with a thing for fine details, so this is literally killing me)

Info that might help u help me :) :
I have nVidia 9200M GS (HP laptop)
I've set nVidia setting to sync vblank and disabled it in compiz
I've also disabled PowerMizer..

I love the system to give up some vsync issues in moving windows, but i just can't get over video tearing..

I'm ready to install anything, change anything, even do a new clean install to get it working.
I will appreciate any ideas.
thnx.

UPDATE: Installed SMPlayer, works fine but drops couple of frames every 5 secs or so (more annoying than tearing lol)

is there any specific settings that can fix that?

---

### Post by SeijiSensei on 2010-10-23
> **Linux_FTW said:**
> I have nVidia 9200M GS (HP laptop)
I've set nVidia setting to sync vblank and disabled it in compiz
I've also disabled PowerMizer.

What player are you using?  Try installing "smplayer" from the repositories and see if that helps.

One problem is that NVIDIA's [VDPAU]("http://en.wikipedia.org/wiki/VDPAU") method for off-loading video decoding to the GPU only works for some codecs.  In particular, XviD/DivX is only supported with more recent cards starting with the GT 2xx series.  I'm guessing the video inside that AVI is encoded with XviD.

You could transcode the video to H.264 in the MKV container with something like mencoder, but that's a lot of work for one video.

---

### Post by Linux_FTW on 2010-10-23
I tried installing KMPlayer and SMPlayer, but both have an unusual problem

the video is either fully or semi-transparent, which make it quite useless, i tried several ways of output, still no luck.

any ideas?

---

