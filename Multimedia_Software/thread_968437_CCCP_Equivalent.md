---
title: "CCCP Equivalent"
date: 2008-11-02
forum: Multimedia Software
---

### Post by Ciwan on 2008-11-02
Hi Guys

I've just installed Ubuntu on my PC, and I want to play some AVI and MKV movies on it.

On my Windows PC ( I have two PCs) I use the CCCP codec pack. I have found it to be the BEST EVER.

I was wondering is there an equivalent to CCCP for Ubuntu ??

Thanks

---

### Post by shirilover on 2008-11-02
That would MPlayer with the SMPlayer front-end. See here -> [http://smplayer.sourceforge.net](http://smplayer.sourceforge.net)

---

### Post by Ciwan on 2008-11-06
Cool thanks Shirilover

Is there a code I can type into a Terminal that would download and install SMPlayer for me ?

Thanks

---

### Post by kostkon on 2008-11-06
> **Ciwan said:**
> Cool thanks Shirilover

Is there a code I can type into a Terminal that would download and install SMPlayer for me ?

Thanks
You can install it using Synaptic...

---

### Post by kostkon on 2008-11-06
As far as a CCCP equivalent, if you have all the *Gstreamer* plugins and the *w32codecs* you can play everything...

---

### Post by shirilover on 2008-11-06
> **kostkon said:**
> As far as a CCCP equivalent, if you have all the *Gstreamer* plugins and the *w32codecs* you can play everything...

But, you won't display styled subtitles properly.

---

### Post by carmy on 2008-11-06
i will search that for you and than give you reply.
Thanks

---

### Post by kodoku on 2008-11-06
> **shirilover said:**
> But, you won't display styled subtitles properly.

The latest stable mplayer has built-in support of a$$/ssa subtitles, which works beautifully in my experience, even for Chinese subtitles =). The only quirk is that you need to have freetype installed as well, but that's as easy as apt-getting.

In short, install Gstreamer codecs and w32codecs, and then install SMPlayer, and you should be good to go!

Note: I forgot about the text filter, a$$ stands for advanced sub station, or .a s s, without the spaces =D

---

### Post by ichi@YUKI on 2009-01-10
i've been looking for this.. thanks.. :D

---

