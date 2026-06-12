---
title: "How could i see Videos for Windows media Player?"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by amonsul on 2006-12-30
Hi!

is there a way to see Windows Media Player Videos in Ubuntu???

Look here for example (italian newspaper):

[http://multimedia.repubblica.it/home/515050]("http://multimedia.repubblica.it/home/515050")

---

### Post by pseudonym on 2006-12-30
If you want to watch embedded windows media you can do so with the mplayer mozilla plugin package and w32codecs. Read all about it in the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") wiki :)

---

### Post by amonsul on 2006-12-30
I've tried all, but it doesnt work. Could someone try to look the video from the newspaper website above???

The same happens with the websitw form apple. 
[http://www.apple.com/de/getamac/ads/]("http://www.apple.com/de/getamac/ads/")

---

### Post by pseudonym on 2006-12-30
> **amonsul said:**
> I've tried all, but it doesnt work. Could someone try to look the video from the newspaper website above???

The same happens with the websitw form apple. 
[http://www.apple.com/de/getamac/ads/]("http://www.apple.com/de/getamac/ads/")
I don't have this stuff installed at the moment, but some questions -

1. Are you running 32-bit or 64-bit version of Ubuntu?

2. Do you get any messages when you try and play the videos?

---

### Post by amonsul on 2006-12-30
32 bit Edgy on a Core 2 Duo with Nvidia Graphics.

I post 2 screenshots...

---

### Post by pseudonym on 2006-12-30
What programs did you install? The ones which most people use for this are mozilla-mplayer and w32codecs. Was it working before and it just stopped?...

---

### Post by amonsul on 2006-12-30
I have installed mozilla-mplayer and then w32codecs through "automatix". No it doesnt work.

---

### Post by pseudonym on 2006-12-30
In that case it could be that those websites are showing videos using a very recent version of the codec that is not currently supported by the w32codecs package (it plays most things, but not always everything).

Unfortunately I can't test this for myself at the moment. sorry.

anyone else?

---

