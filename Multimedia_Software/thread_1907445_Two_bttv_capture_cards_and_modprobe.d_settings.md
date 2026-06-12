---
title: "Two bttv capture cards and modprobe.d settings?"
date: 2012-01-11
forum: Multimedia Software
---

### Post by Twizzle on 2012-01-11
I have zoneminder installed on Ubuntu x64 10.04 server edition with a generic Bttv card.

From the zoneminder and a number of other forums, i have created a file in /etc/modpbobe.d called bttv_zm with the following code:

```
		
options bttv gbuffers=32 card=77 tuner=4 radio=0 coring=1 full_luma_range=1 chroma_agc=1 combfilter=1 autoload=0 triton1=0 vsfx=0	

```

Everything works fine with two cameras.

I have now obtained a second generic card which is (i think) pretty much identical. (There is a heatsink over the chip on this one so I cant check it is the same make)

When running zm, however, the colour is very poor on the second card which is I assume due to not having the correct settings for it in the modprobe file.

Could someone please explain how I go about adding settings for a second card. They are video0and video1 respectivley.

---

