---
title: "Is it possible to rip part of a vob?"
date: 2009-10-01
forum: Multimedia Software
---

### Post by David_UK on 2009-10-01
Hi
I have been using DVD::Rip to create vob files on my HDD from commercial DVDs.  Then I use ffmpeg to encode as desired.
I usually want just a short clip of the movie so I'd prefer a ripper that would allow just part of a dvd vob to be copied (I guess it would need a preview facility to allow me to get the right frames).  Is that possible, or is it best to always rip a whole vob?

Thanks

---

### Post by cor2y on 2009-10-01
As far as I know you cant parially rip like say a half/third of a vob since they are structed in sections.
it depends on how the dvd is authored for example the part you want might be on one vob file or split across two or more.
In those cases you can rip the specific vob file using vobcopy and then encode that section using mencoder, avidemux or ffmpeg, if for example you only wanted the first five mins and not the rest of the file or the last 10 mins then you can specify where, with any of those tools, to  begin/end the encode.

---

### Post by blur xc on 2009-10-01
> **David_UK said:**
> Hi
I have been using DVD::Rip to create vob files on my HDD from commercial DVDs.  Then I use ffmpeg to encode as desired.
I usually want just a short clip of the movie so I'd prefer a ripper that would allow just part of a dvd vob to be copied (I guess it would need a preview facility to allow me to get the right frames).  Is that possible, or is it best to always rip a whole vob?

Thanks


I've been trying to do the same thing for some time now- and finally found a soulution.

It's maybe not the best solution, but it's worked for me.  I use Handbrake to rip the dvd into whatever format I want, and I used kdenlive to cut out the clip I wanted.  

What I haven't tried, is to just rip a chapter off of the dvd.  I think there's  the option to rip the entire dvd or chapter by chapter...  But you'd need to know what chapter you wanted off of your dvd.

BM

---

