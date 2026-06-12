---
title: "Xine engine suddenly won't play most video streams"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by Phil Urich on 2007-02-27
Humorously, my first attempt at a post died because as soon as I hit "close window" in the attachment selection window it crashed my Konqueror window.

So yeah, I'm running Kubuntu Edgy AMD64.  And suddenly xine has stopped working, specifically, the xine engine appears unable to render any video streams other than mpeg's 1 and 2. 

So, VOB files (and DVDs themselves) play fine; .ts files capped from HDTV streams are also a-OK.  Old old .mpg files tend to be just fine, though naturally still of bad quality ;)

But anything encoded in XviD won't work; anything encoded in any version of DivX won't work (from the old stolen-from-microsoft DivX3 to DivX6), in fact I have yet to come across an AVI file that'll play the video (even the MJPEG encoded .avi files from my digital camera are a no-go).  I've tried .asf files (WMV9 to be specific), no dice there either.  x264-encoded videos in a Matroska container?  Nope.  The list probably goes on, but I'm starting to run out of types to test!

This unfortunately eliminates my two favorite video players (Kaffeine and Xine-UI); KMplayer didn't work for a bit, but of course it worked fine after I switched it to use mplayer as its engine.  Similarly the somewhat cumbersome VLC player plays video just as it always has.  Audio is no problem at all.

I've tried "aptitude reinstall" on every package I could think of, and outright removed xine-ui and reinstalled just in case.  None of this has worked.

I've attached some files; these are parts of bug report files (a full single file would be over the limit for this forum, alas).  BUG-REPORT-1 and BUG-REPORT-2 are the first two sections of the debug file, the parts that stay the same (as far as I can tell) regardless of what file is being loaded, as far as I can tell.  The remaining files are the last section of the debug logs where it's actually loading the file and playing it back.  All of this was gleamed by running "xine --bug-report {filename}".

Any ideas?

---

### Post by panch0 on 2007-02-27
Since you are on Kubuntu, one thing you can do is try KPlayer. It uses MPlayer as the backend, and in many ways it is a good bit more advanced than Kaffeine. And it is more stable too, in fact I can't recall a single crash from it.

---

### Post by Phil Urich on 2007-02-27
> **panch0 said:**
> Since you are on Kubuntu, one thing you can do is try KPlayer. It uses MPlayer as the backend, and in many ways it is a good bit more advanced than Kaffeine. And it is more stable too, in fact I can't recall a single crash from it.

Well, by default it actually uses Xine nowadays (at least it was on my computer).  I did switch the backend to MPlayer and that's how I've been using it.  However, while the MPlayer engine might be more stable it is nonetheless a bit less featured from what I can tell . . . or at least it doesn't react in ways I've grown used to (this is coming from the difference switching KMPlayer and Kaffeine between the engines).  Furthermore I'd rather use Xine-UI as a player, and naturally that only works with the xine engine!  So I'd really rather just get the xine engine fixed.  There must be some way to do a more complete reinstall, or some possible explanation as to what went wrong?

---

### Post by panch0 on 2007-03-02
> **Phil Urich said:**
> Well, by default it actually uses Xine nowadays (at least it was on my computer).  I did switch the backend to MPlayer and that's how I've been using it.  However, while the MPlayer engine might be more stable it is nonetheless a bit less featured from what I can tell . . . or at least it doesn't react in ways I've grown used to (this is coming from the difference switching KMPlayer and Kaffeine between the engines).  Furthermore I'd rather use Xine-UI as a player, and naturally that only works with the xine engine!  So I'd really rather just get the xine engine fixed.  There must be some way to do a more complete reinstall, or some possible explanation as to what went wrong?

You are confusing KMPlayer and [KPlayer]("http://kplayer.sf.net/"). KPlayer is much more advanced as a standalone player, and only uses MPlayer as the backend, which I think is why it can make the most out of it. Definitely try it out.

---

### Post by Phil Urich on 2007-03-03
> **panch0 said:**
> You are confusing KMPlayer and [KPlayer]("http://kplayer.sf.net/"). KPlayer is much more advanced as a standalone player, and only uses MPlayer as the backend, which I think is why it can make the most out of it. Definitely try it out.


Oh!  Thank you for pointing that out, I had indeed just assumed since it didn't show up in Adept for some reason...apparently, though, I even already had it installed.  Hmm.  I'll have to make a menu entry for it, I guess.  Odd that there wasn't one.

Thank you for that!

Not to sound whiny, though, but:

(1) I still would kinda like to use Xine-UI.   Also,
(2) Still no thumbnails  generated for these videos.

I know this sounds nitpicky . . . but I do wish to actually <I>fix</i> this, instead of just working around it.  I'll admit, I'm starting to lose hope.

At least I'll be able to use KPlayer to watch videos while my hope wanes ;)  Silver lining, I suppose!

---

### Post by kamazu on 2007-03-11
Did you try to delete the .xine directory, this did it once for me, despite of all reinstalling, upgrading etc....

hope you solved it

cheers 
kamazu

---

### Post by Phil Urich on 2007-04-25
It mysteriously fixed itself on its own, actually.  Or to be more specific, in the process of using avidemux it seemed to have started things working again.  Considering it was while using avidemux that it had stopped in the first place, upon further reflection, it does make at least a little bit of sense.   Deleting the .xine directory is a good idea, though, I can't believe that didn't occur to me (I'll definitely keep it in mind for if this happens again).

Switched over to Feisty now, though, and Xine isn't one of the (very few) problem areas, so hopefully this is all resolved for the foreseeable future.  I've still got a feeling it had to do with AMD64, all the problems I ever seem to have with Ubuntu seem to stem from the second-class nature of how 64-bit is still being treated in the software world.

---

### Post by inportb on 2007-05-07
Wow, thank goodness this post is around. I had trouble playing divx videos until I cleaned up .xine  =D
Thanks for the tip.

---

