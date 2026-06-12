---
title: "Legal VIdeo Editing Options For US?"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by Sand Lee on 2007-07-27
I live in the USA and I was wondering if there is was any legal video editing software that I can use? 
My digital camera encodes it's videos in Motion JPEG ==> .AVI.  Surprisingly Ubuntu could see the video w/ out installing illegal codecs!! I've tried Kino but that only works for DV.

---

### Post by RomeReactor on 2007-07-27
Hi. You could use [AviDemux]("http://en.wikipedia.org/wiki/Avidemux"). As [.AVI]("http://en.wikipedia.org/wiki/AVI") is just the container, what would interest you would be what codecs it's using (try right-clicking on your avi file, select "Properties" and go to the "Audio/Video" tab); if the video codec is [MPEG-4]("http://en.wikipedia.org/wiki/MPEG-4#Licensing"), you may be able to decode it with either [Libavcodec]("http://en.wikipedia.org/wiki/FFmpeg#Legal_status") or [Xvid]("http://en.wikipedia.org/wiki/Xvid#Legal_issues"), which are free/open source software, though, as you can see there *may* be legal issues attached to them. Or you may buy licenses for Gstreamer decoders/encoders from [Fluendo]("https://shop.fluendo.com/").

However, if as you say Ubuntu could play the video without installing any extra codecs, it's probably OK to use AviDemux to edit your file, as more likely than not the codecs it has have free, open source, and **legal** implementations already installed in Ubuntu.

Having said that, I am in no way an expert on this subject, so you should do some searching of your own on this issue. If you decide to go ahead and use AviDemux, you can find it through Synaptic (System->Administration->Synaptic Package Manager), Add/Remove, or install it from the terminal (Applications->Accessories->Terminal):
```
sudo apt-get install avidemux
```

---

### Post by Sand Lee on 2007-07-29
Thanks RomeReactor!

---

