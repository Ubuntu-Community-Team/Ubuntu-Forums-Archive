---
title: "[SOLVED] Kdenlive: Video and Audio out of sync."
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by Motorhead Kaze on 2007-11-11
Hello. I just upgraded to Gutsy, in general, so that I could get Kdenlive from the repos and start making DVDs. I used Kino to convert my MP4's to DV files, then imported them to Kdenlive.  But since then many, many hours have gone by.

It seems that no matter what I try to produce, whether it be .avi, mpeg, or quicktime all come out with the same result: Video is more jerky than the original, sound is crackly, and the REAL problem is THE VID AND SOUND ARE OUT OF SYNC.  Just to be sure, I burned a DVD and got the same result.  I've reviewed the .dv files I made and they are fine.  

I could use some help on this one. I'm already hours into this, and need some help. Thanks much.

---

### Post by stbub on 2007-11-17
Been trying to use kdenlive for a while.

I managed to edit my video by hitting save constantly due to constant crashes.

If I play the video in kdenlive it is ok.

If I try to export it, the exported video/audio isn't anything that it ought to be.

Did some googling, and started kdenlive as follow:

MLT_NORMALISATION=NTSC kdenlive

Looks like the kdenlive folks are in europe, and don't do much testing with ntsc.

With this, it looks the video for the dvd export is ok (though I think the creation of the dvd structure is wrong)

As for exporting the timeline, I'm still out of luck.  Even with MLT_NORMALISATION=NTSC, the video resolutions are PAL (e.g. for XVid I can get 720x576 whereas for ntsc it is supposed to be 720x480)

BTW, I tought about signing up on the kdenlive forum, but then there legal notice is non-sense.  Something like "if you use the forum, then you agree to the terms, oh, and we may well change it, so you really ought to check back often the terms of the conditions, 'cause you've already agreed to future terms".  Geeze...

---

### Post by stbub on 2007-11-17
Well, looks like MLT_NORMALISATION=NTSC isn't sufficient.  The exported video was fine until it got to the second clip.

5 thumbs down.:(:(:(:(:(

Oh well, I guess I'm not gonna be doing much video editing anytime soon.

---

### Post by Motorhead Kaze on 2007-11-17
Oh!  Hohoho.  I just came back to this thread to say, "My friend found this [http://www.kdenlive.org/mantis/view.php?id=23](http://www.kdenlive.org/mantis/view.php?id=23) " and here you were waiting for me with your reply.  Thanks though!  I'm going to go ahead and post this link for... some reason.

Thanks.

---

### Post by Motorhead Kaze on 2007-11-17
Saint Bub,

Well, my tests came up shite.  I tried to go through the terminal into Kden and my vids came up black with no sound.  Crapity crap.

BUT!  What may work is just using Kino for everything.  Playing around with it today it appears yes, we can splice the vid files together (with that icon that looks like 2 arrows pointing at a bar) and can even add text to the vid.  I don't know if it will be cool text like in Windows Movie Maker but under FX, Video Filter tab, just change "No change" to ...something you like, such as "Titler" (adds text).

Then export the movie as mpeg or whatever.  What I don't know yet is if the Mpeg is going to be PAL or something else.  But I'll give it a try.  Anyway, Kino doesn't appear to be as useless as Kdenlive.

Update: Turns out Kden had issues with Gutsy.  Damn.  Gave up and used Moviemaker that time.  Damn.

---

