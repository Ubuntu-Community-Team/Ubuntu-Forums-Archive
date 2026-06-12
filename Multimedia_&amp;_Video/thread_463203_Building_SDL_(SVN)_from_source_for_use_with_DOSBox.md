---
title: "Building SDL (SVN) from source for use with DOSBox"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by chmmr on 2007-06-03
There is a bug in the version of libSDL in the Feisty repositories that causes [this](http://vogons.zetafleet.com/viewtopic.php?t=15393) bug in DOSBox.  There's a simple fix for Windows users, which is to use a version of SDL.DLL compiled from the latest source (which a guy on the Vogons forums has so kindly made available).  I would like to use the analogous fix in Ubuntu, but I'm not 100% clear on how to go about it.

I notice that there is a special version of SDL for Debian / Ubuntu, and I was wondering if I was treading into rough territory here - I was able to get the latest SDL to build, so I'm wondering how I get DOSBox (and [i]only[i] DOSBox, so other apps don't screw up) to use that version of the lib rather than the main one in /usr/lib ?

---

