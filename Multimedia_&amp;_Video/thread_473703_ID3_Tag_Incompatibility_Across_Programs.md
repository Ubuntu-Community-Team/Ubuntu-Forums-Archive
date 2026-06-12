---
title: "ID3 Tag Incompatibility Across Programs"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by RSL on 2007-06-14
This is kind of annoying but it seems like every other audio tool uses a different version of id3v2. Soundjuicer hosed every single CD I ripped from my collection when it used id3v2.4 which WMP doesn't understand and seems to just ignore.Audio Tag Tool and EasyTag both see the id3v1 tags on some other files but I don't want to have to manually add the extra characters that that version cuts off. Is there no way to downgrade the version number or something so that my validly tagged id3v2.4 files can be read as id3v2.3 ?

I'd really hearing how anyone else got/gets around this problem.

---

### Post by RSL on 2007-06-15
Am I the only one who has this problem??

---

### Post by ske1fr on 2007-06-15
> **RSL said:**
> This is kind of annoying but it seems like every other audio tool uses a different version of id3v2. Soundjuicer hosed every single CD I ripped from my collection when it used id3v2.4 which WMP doesn't understand and seems to just ignore.Audio Tag Tool and EasyTag both see the id3v1 tags on some other files but I don't want to have to manually add the extra characters that that version cuts off. Is there no way to downgrade the version number or something so that my validly tagged id3v2.4 files can be read as id3v2.3 ?

I'd really hearing how anyone else got/gets around this problem.

If by "manually add the extra characters" you mean the ones that are cut off the v1 tags then there's nothing you can do - v1 tags only allow 30 characters each for album, title artist and comment.  If you mean having to repopulate the id3v2 tags by copying the id3v1 tags (or vice versa) then again - not much you can do. 

Have you tried Kid3?  Seems to allow converting v2.4 to v2.3 and vice-versa, though I haven't needed that myself.

---

### Post by maubp on 2007-06-15
I had this too - What gstreamer profile are you using with Sound Juicer?

I remember finding a page online suggesting it can be made to write both ID3 v1 and v2.4 tags (but sadly for us, not v2.3 tags).

I care because my in car mp3 CD player doesn't recognise ID3 v2.4 tags (but I think it can read v1 or v2.3)

---

### Post by gantengx on 2007-06-19
The best is to use id3v2.3. afaik kid3 can't convert between id3v2.4 id3v2.3.

So what i do is use id3v2.4 and then convert it back to id3v2.3 using eyeD3

[http://eyed3.nicfit.net/](http://eyed3.nicfit.net/) 

and it works fine :D

---

