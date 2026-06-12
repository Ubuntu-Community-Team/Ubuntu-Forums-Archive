---
title: "How do I create a DVD Video?"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by Makurosu on 2006-12-26
I've done some searching around the forums, and I can't seem to find an answer to this question.

How do I create a DVD Video?  I already have the VOB files and file structure ready, so I don't need a DVD authoring program.  All I need is to copy my files to the DVD.  I've already tried creating a data DVD with GnomeBaker, and the resultant disc will not play on my DVD player.  In Windows, I would use Nero, add my files, and burn a DVD Video.

I've also looked at K3b, dvd:rip, acidrip, and DeVeDe.  I don't need to rip, convert or author - just burn a DVD Video from my VOB files, VIDEO_TS.IFO, etc.  It's already ready to go.

It seems like such a simple thing, and yet I can't seem to find a tool to help me do it.

Thanks in advance.

---

### Post by tagra123 on 2006-12-26
> **Makurosu said:**
> I've done some searching around the forums, and I can't seem to find an answer to this question.

How do I create a DVD Video?  I already have the VOB files and file structure ready, so I don't need a DVD authoring program.  All I need is to copy my files to the DVD.  I've already tried creating a data DVD with GnomeBaker, and the resultant disc will not play on my DVD player.  In Windows, I would use Nero, add my files, and burn a DVD Video.

I've also looked at K3b, dvd:rip, acidrip, and DeVeDe.  I don't need to rip, convert or author - just burn a DVD Video from my VOB files, VIDEO_TS.IFO, etc.  It's already ready to go.

It seems like such a simple thing, and yet I can't seem to find a tool to help me do it.

Thanks in advance.


Piece of cake using the terminal.

```
growisofs -speed=1 -Z /dev/hda -dvd-video /path/to/DVDfiles
```  

/dev/hda is my dvd drive  ----  /dev/dvd will usually work too


The path to DVDfiles should contain the AUDIO_TS and VIDEO_TS folders. Your VOB files should be in VIDEO_TS

K3B should also do this for you. It is very similar to nero.

---

### Post by Makurosu on 2006-12-27
> **tagra123 said:**
> Piece of cake using the terminal.

```
growisofs -speed=1 -Z /dev/hda -dvd-video /path/to/DVDfiles
```  

/dev/hda is my dvd drive  ----  /dev/dvd will usually work too


The path to DVDfiles should contain the AUDIO_TS and VIDEO_TS folders. Your VOB files should be in VIDEO_TS

K3B should also do this for you. It is very similar to nero.

Ahh!  How could I have missed that?  I was looking at the buttons in K3b and didn't look in the menus.

Interesting about the terminal method.  I always make my discs the same way.  I could just write a little script and not have to fuss with a UI.  Thanks for the tip.

---

### Post by Doug11 on 2007-01-04
wow,,I missed that too. Was looking for the same type of thing.

---

