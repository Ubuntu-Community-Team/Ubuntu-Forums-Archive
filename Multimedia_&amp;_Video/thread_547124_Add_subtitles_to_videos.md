---
title: "Add subtitles to videos"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by Hospadar on 2007-09-09
Hi,
I have some old videos I want to add subtitles to, and I also have some subtitle files for the videos.  I can use gnome subtitles to view the subtitles so I know they work, but I want to permanently add the subtitles to the videos so I don't need a special player to watch them with the subtitles (I'd like to be able to watch them on my zen vision).

I'd really appreciate any help with this, I've been looking for a good copy of these videos for a while.

Thanks!

---

### Post by u-slayer on 2007-09-09
avidemux can do this

Just...

sudo apt-get install avidemux

Launch avidemux

Change your codec to x264

Click filters and select subtitles.

---

### Post by Hospadar on 2007-09-09
Ok, so I've done this, and I can see the subtitles in the preview but I don't know how to actually put them in the file.  I can save the file, but that just copies the original file.  I'm sure i'm missing something obvious with exporting but I can't for the life of me figure out what it is.

Also, I can't seem to get any filters to stick.  I tried a desaturation one just to check but that didn't do anything either.

It's an xvid movie with .*** subtitles (although i could just as easily put them in some other format)

---

### Post by bwal831 on 2008-06-19
I had the same problem with the subtitles, but I think I figured it out.  The default location for the subtitle font is incorrect.  Pick a font from /usr/share/fonts .  I think it should work after that.  I don't know about your other filter problems.

---

