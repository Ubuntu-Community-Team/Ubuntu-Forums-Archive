---
title: "gstreamer extra plugins legal in U.S.?"
date: 2008-04-22
forum: Multimedia Software
---

### Post by billdotson on 2008-04-22
Are the gstreamer extra plugins legal in the U.S.?

Also, why did following the information from this website: []("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html")
not provide me with all the necessary codecs?

Thanks.

---

### Post by cor2y on 2008-04-23
I believe they are since gstreamer only decodes and does not allow you to encode to the formats in question.
Are we talking about the free plugins or the pay ones from fluendo?
As far as I know both are legal since they were reverse engineered and don't touch any proprietary work.
Like the w32codecs for mplayer.
But i am not a patent or copyright expert, also in the case of the w32codecs you are allowed to use them if you have a copy of windows i believe.

You can find all the gstreamer plugins right in synaptic, they are not installed by default thats all.
The universe repo i believe must be enabled.

---

### Post by billdotson on 2008-04-24
I am talking about the free codecs, not the paid Fluendo ones; those are pretty expensive.

---

### Post by Greenbean209 on 2008-04-24
Sorry this kinda unhelpful post but (i don't know if it matters to  you) does it matter if its legal in U.S. anyway... I'm mean I'm pretty sure you want get arrested or anyhting

---

### Post by cor2y on 2008-04-24
The paid ones give you updates (lifetime i believe) and they are always ahead of the opensource version ones.
Like the fluendo wmv version can correctly decode vc-1 simple and complex encoded files as well as wma pro audio.
The opensource gstreamer plugins can only partially correctly decode the vc-1 profile as well as wma audio, you still see visual artifacts if the file was encoded with a complex vc-1 profile and get audio skips or sometimes even no audio in wma pro encoded files.

---

