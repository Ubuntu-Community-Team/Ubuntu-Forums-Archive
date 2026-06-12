---
title: "granulepos errors ripping to ogg using abcde"
date: 2010-06-21
forum: Multimedia Software
---

### Post by krivine on 2010-06-21
I recently finished ripping my CD collection. Some of the files don't
play; VLC and other players can run them, but there's no sound. Running
oggz-validate shows errors like this:

        granulepos 0 on page with no completed packets

(I didn't know about oggz-validate when I was ripping, otherwise I'd
have checked as I went.)

I can't see a pattern: with some CDs it's the whole CD, with others,
just some tracks.

I pretty much ran with the default abcde options. I upped the quality at
one point, but dropped it back again. 

Before I replace the bad files, does anyone have any advice on what to
do or avoid? I've tried googling the error, but haven't found anything
useful.

---

### Post by krivine on 2010-08-14
It's possible that the errors happened after ripping, when I ran Songbird to fill in the album art metadata. 

I've no granulepos errors at the moment, but occasionally find 'bad vorbis header' errors, which oggz-validate doesn't pick up. For these errors, running the files through soundconverter (ogg > ogg) worked.

---

