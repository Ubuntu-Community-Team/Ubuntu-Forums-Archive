---
title: "App to edit photo time stamps?"
date: 2009-09-18
forum: Multimedia Software
---

### Post by karamu on 2009-09-18
I have a rather annoying problem with my photos- the date/ time stamps of all the files are wrong. This means that if I try to organise my photo collection using GSpot it thinks they were all taken at the same time.

Can anyone recommend an application I can use to edit the dates fo the photos (in batches- it would take forever to do individually)?

---

### Post by quixote on 2009-09-19
How is your photo program listing the files?  By modification date?  Because usually you can list by creation time (sometimes called "exif time"), which is probably what you're looking for. (?)

If GSpot doesn't have that option, try some of the others.  Personally, I don't care for F-Spot or Digikam.  The best I came across was Gwenview, which is a KDE program.  (You can run it under gnome, but it will also install a number of kde libraries it depends on.)  I use gthumb (because I don't have enough space for the extra libs used by gwenview).

Or did you mean something else entirely, and this is all old news?

---

### Post by karamu on 2009-09-22
Thanks for the suggestions. I was meaning of course F-spot (Gspot- Freudian slip??!).

When I import photos into it the program thinks most of the pictures are from either 1980 or 2008! Then if I check the file properties, the creation date is all zeros.

I think the problem is probably my camera- it is an old crappy one which runs on regular AA batteries. I intend to replace it with something next year but I need something to edit my existing collection's date/ time stamps.

---

### Post by quixote on 2009-09-22
I use something called geotag, because my camera doesn't store GPS coordinates and I needed something to add those to the exif data in batches.  Very similar problem, so I checked to see whether it would change time stamps, and it does.  You can change time manually on one file, and then copy that to all the files currently loaded.  I think you can only do it directory by directory, not recursively.

Geotag itself ([http://geotag.sourceforge.net/?q=node/12](http://geotag.sourceforge.net/?q=node/12)) is a bit fiddly.  It requires java, you use a specific java command to start it, and when it starts, nothing seems to be happening for a while.  Then there's no indication what to do.  Go to File > Add images from directory.  But once you're past the quirks, I haven't found anything else as usable for dealing with exif data.

---

### Post by karamu on 2009-09-24
OK, thanks for the tip- it sounds like that should do what I want.

I'll let you know how I get on- cheers for that!

---

### Post by karamu on 2009-09-24
OK, I'm going to sound like an idiot but how do I install Geotag? I installed Java runtime and downloaded the Geotag tar.gz but I'm not sure what to do with it....

What do I need to do?

---

