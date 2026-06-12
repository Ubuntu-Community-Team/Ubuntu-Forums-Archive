---
title: "Can't play british DVDs"
date: 2011-06-12
forum: Multimedia Software
---

### Post by miki_cz on 2011-06-12
Hey, i've bit of a problem.

I've bought some Doctor Who DVDs in UK and now, i cant play it here at home (Czech Republic). I tried defferent DVD's and they work just fine.

I've tried install medibuntu and libdvdcss and it still doesn't work.

Please help.

---

### Post by handy on 2011-06-12
The world has been divided up into sections & given numbers called region codes, this may be causing your problem:

[http://en.wikipedia.org/wiki/DVD_region_code](http://en.wikipedia.org/wiki/DVD_region_code)

---

### Post by coffeecat on 2011-06-12
Both the Czech Republic and the UK are in the same region 2, so that's puzzling.

However, handy makes a good point. @miki_cz, where in the UK did you buy them? From a reputable retail outlet or online store, or somewhere where rogues might be operating such as a street market or car boot sale? The reason I ask is that you may have been ripped off with region 1 imports or something like that.

What does it say about the region on the packaging? Were you able to play them in the UK? Have you tried them in another player?

---

### Post by miki_cz on 2011-06-12
I've bought them in HMV shop (hmv.com). 

On the box is written **2 + 3 Colour PAL UK**.
I tried them play in two different dvds and they work fine...

---

### Post by coffeecat on 2011-06-12
OK, the DVDs are OK and they play in other DVD players. Let's look at the machine they won't play in. You say other DVDs play OK in that machine, or did you mean in your first post that you tried the DVDs in other machines? It sounds from your wording as though other DVDs (discs) were playing in the machine that the Dr Who DVDs wouldn't. 

I'll assume that you meant that you tried the Dr Who DVDs in another machine, not that other DVDs will play in the machine that won't play the Dr Who ones. In which case you need to install libdvdread4 and some codecs. The easiest way is to install the package ubuntu-restricted-extras - which will also bring in some unrelated stuff such as Microsoft core fonts. Also, you might consider installing VLC which is excellent for playing DVDs.

---

### Post by miki_cz on 2011-06-12
To make it clear: Disc, which i can play in DVD(device), doesn't work at my laptop. 

I have installed vlc, ubuntu-restricted-extras, libdvdread4 and still doesn't work...

---

### Post by rajeevisonline on 2012-10-16
One last things you must try:

This adds the medibuntu repos but still give it a try... I think you might be missing a codec or two

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-on-ubuntu-11-10-oneiric.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-on-ubuntu-11-10-oneiric.html)

Please reply and Ill think of something else

---

### Post by oldos2er on 2012-10-16
Old thread closed.

---

