---
title: "Apple Quicktime and Edgy .mov"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by stchman on 2007-05-04
Hello all I have a question about being able to play .mov files.

I use VLC and it plays everything I throw at it with near zero problems EXCEPT .mov files.  I have an assortment of .mov files and some play (with no sound) and others refuse to play at all.  Is there a gstreamer plugin that is needed?  According to VLS it plays QT stuff out of the box.

Thanks

---

### Post by apunc1 on 2007-05-04
i'm not familar with VLC  but mplayer plays .mov files for me

---

### Post by stchman on 2007-05-04
> **apunc1 said:**
> i'm not familar with VLC  but mplayer plays .mov files for me

Did you have to install a particular gstreamer?

---

### Post by stchman on 2007-05-04
Would this work?

wget [http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb)
sudo dpkg -i w32codecs_20061022-0medibuntu1+build1_i386.deb

The w32codecs .deb package appears to support .mov and .rm with mplayer.

One thing is that the package is for feisty, if you go to their website they have a w32codec for Edgy.  Anyone have any experience with this package?

Thanks.

---

### Post by apunc1 on 2007-05-05
> **stchman said:**
> Did you have to install a particular gstreamer?

I actually can't remember if I had to install gstreamer plugins specifically for mplayer. I think it played everything by default, but I do have these gstreamer plugins installed

plugins-ugly
plugins-good
mad (the mad audio decoder for mpeg)
plugins-base

i'm still using dapper. mplayer plays everything for me but often I have to force quit it. and if i'm in full screen mode I have to restart X manually. kind of a pain, but it does play everything ;)
that might be a dapper bug that was fixed in later versions. i haven't really looked.

---

### Post by stchman on 2007-05-07
> **apunc1 said:**
> I actually can't remember if I had to install gstreamer plugins specifically for mplayer. I think it played everything by default, but I do have these gstreamer plugins installed

plugins-ugly
plugins-good
mad (the mad audio decoder for mpeg)
plugins-base

i'm still using dapper. mplayer plays everything for me but often I have to force quit it. and if i'm in full screen mode I have to restart X manually. kind of a pain, but it does play everything ;)
that might be a dapper bug that was fixed in later versions. i haven't really looked.

Does all your Quicktime .mov files play and does the sound work?

Thanks

---

### Post by apunc1 on 2007-05-07
> **stchman said:**
> Does all your Quicktime .mov files play and does the sound work?

Thanks


yes

---

