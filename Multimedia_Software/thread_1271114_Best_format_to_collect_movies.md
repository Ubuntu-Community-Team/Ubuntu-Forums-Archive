---
title: "Best format to collect movies"
date: 2009-09-20
forum: Multimedia Software
---

### Post by StuartN on 2009-09-20
I have a few hundred movies and home videos backed up from DVD onto hard disk, in the original mpeg file format. Each is a single .VOB file created from the multiple VOBs on the DVD with no transcoding and no menus, but I did manually split some stuff into "episodes". (The home movies are the same, as I transferred from analogue via a DVD recorder).

What is the best format for maintaining and growing this collection? I could either buy more hard disk space and retain the mpeg2 VOB format or compress them further, in which case I need to choose a compression format.

If I compress them further then I would need to a) retain the quality, b) make sure they play directly on my TV equipment (plays all ordinary DVD, DIVX/XVID etc), c) can be transcoded to iPod format and d) be sure that the compressed format will be as well supported in the future as mpeg2.

Note that continuing to keep the collection as .VOB files meets all these criteria.

---

### Post by diddy1234 on 2009-09-21
I would say go with converting them to Xvid.

The reason for this is that even in windows Xvid is quite well supported now (Win 7 supports this out of the box).

I had films in various formats taking up nearly 300Gb, so I used mencoder and converted to Xvid (it took quite a while to do) and I saved alot of space.

Hope it helps.

---

### Post by StuartN on 2009-09-21
> **diddy1234 said:**
> I used mencoder and converted to Xvid

Do you have any suggestions on the settings - bit-rate, audio encoder, etc? I will probably use Avidemux because I'm a wimp, but it will be the same outcome.

---

### Post by colemar on 2009-09-21
Given the quick and steady drop of hard drive prices, I think it is not convenient to take the hassle and the time involved in transcoding.
Transcoding can be amusing for the first few days ("Look how cool I am!"), but sooner or later you will find yourself wondering if the cpu and your time can be devoted to better tasks.

If you insist in doing it, I believe the only two choices that make sense are:
- divx in AVI
- h264 in Mastroska
Don't try to squeeze the movies under 50% of the original size, or you will be sorry for the lost quality.

---

### Post by diddy1234 on 2009-09-21
I used the following mencoder settings (in a bash script) to encode all films.

It did take a while though to do but quality was not too bad at all.

mencoder -vf scale=720:576 -ovc xvid -xvidencopts bitrate=1200 -oac mp3lame -lameopts cbr:br=160:vol=0 -noskip <INPUT FILE> -o <OUTPUT FILE>

That is what I used

if you were wanting to test the above with some files, you can add -endpos=00:01:00 say to encode 1 minute of video

---

