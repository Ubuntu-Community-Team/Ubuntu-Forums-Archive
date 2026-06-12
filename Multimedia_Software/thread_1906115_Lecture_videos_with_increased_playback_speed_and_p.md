---
title: "Lecture videos with increased playback speed and pitch correction"
date: 2012-01-08
forum: Multimedia Software
---

### Post by apeterle on 2012-01-08
Hi, i would like to convert a video with an increased or decreased playback speed and and pitch correction, using **mencoder** (amd64 arch.).

tutorial:
[http://eeff0c.blogspot.com/](http://eeff0c.blogspot.com/)

$ sudo apt-get install tap-plugins

that commands don't work (mplayer):

mplayer -speed 0.8 -af ladspa=/usr/lib/ladspa/tap_pitch.so:tap_pitch:0:25:-90:0 file.mp3


also mencoder - see the script following the link - doesn't work, with the same issue.


error:
Couldn't find audio filter 'ladspa'
[libaf] Couldn't create or open audio filter 'ladspa'
Error at audio filter chain pre-init!


i set also in .bashrc:
export LADSPA_PATH=$LADSPA_PATH:/home/alex/.ladspa:/usr/local/lib/ladspa:/usr/lib/ladspa


Any idea? 

I found also that post:

hi,
i use ubuntu on **amd64** with ardour and the **TAP plugins did not work**. some months ago i recompiled them and got them working by **switching a compiler option** and mailed it to tom who gave me another solution. here is a part of a mail with tom szilagyi:

>Hi Steve,

>could you achieve the same effect by simply adding
>-fno-strict-aliasing to the GCC options, instead of the above?

>I would be interested in the simplest solution. :)

>So I would just change one line in the Makefile to:
>CFLAGS = -I. -O3 -Wall -fomit-frame-pointer
>-fstrength-reduce -funroll-loops -ffast-math -fno-strict-aliasing -c
>-fPIC -DPIC

>(I just added -fno-strict-aliasing to the end of the -f* list)

>Could you confirm if this works the same as your solution?

>Thanks,
>Tom

this helped me and i work a lot with these plugins as they have a parametric equalizer.

i have similar problems with the holap plugins (exciter !!) on ardour - they still don't work in ardour but in jackrack as i detected now. so for any non-working ardour plugin start jackrack and insert it into the main channel of your mixer, connecting your outs/ins to jackrack, then load the desired plugins into jackrack and test them.

best wishes,
steve

source:[http://ardour.org/node/3002](http://ardour.org/node/3002)

---

