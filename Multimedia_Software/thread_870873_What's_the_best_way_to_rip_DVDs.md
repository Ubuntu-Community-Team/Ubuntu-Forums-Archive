---
title: "What's the best way to rip DVDs?"
date: 2008-07-23
forum: Multimedia Software
---

### Post by bipolaric on 2008-07-23
hi, I am a linux virgin, who has a 2 yr old son with severe learning difficulties, who likes to eat DVD's, he's chewed his way through many of my favorites, of which are now non playable, hence the need to back them up.  In XP it was easy, I used a DVD Decrypter to get the Data, then I used Auto GK to encode the files to .avi format, before using Nero 6 to reproduce the dvd, if needed.  I would like to STRESS, that I am NOT a pirate, and only used these XP programs to back-up my own personal collection.  However, and here is the problem.  I have tried OGM Rip, DVD::Rip, and now I am trying K9Copy. but I want to know the fastest way to rip a DVD.  OGM Rip gave me a timescale longer than 3hrs, which is unacceptable.  I am trying with K9Copy, but I dont know what the hell I am doing, it seems to go through the movie in the preivew then it shuts down. I am currentle using Ubuntu 8.04.1, of which thus far I am mightly impressed with, but can somebody PLEASE ! help me with my problem, as I haven't a clue what I am doing.

Thanks in advance :)

---

### Post by bipolaric on 2008-07-23
tried dvd::rip, i am left with a .rip file, and 7 vob files, what do I do next ?

---

### Post by bipolaric on 2008-07-23
> **unoodles said:**
> My recommendation is to use dvd::rip. DVD::RIP will accomplish both the tasks of copying the .VOB files then converting them to .avi.
K9Copy is more of a program for making archive copies. It is similar to dvdshrink.

You also may want to get GnomeBaker and/or k3b for dvd burning. tried dvd:rip i am left with .rip files and .vob files what do i do next ?

---

### Post by bipolaric on 2008-07-25
I posted a question the other day, but didn't really get a good enough reply.  Basicly I have a 2 yr old son with learning difficulties, who likes to eat DVD's, so I started to back them up in, (spit !) XP.  I used a DVD Decrypter, then Auto GK, the process of which ripped the DVD and converted it into AVI format, which was stored on my hard drive for future burning back to DVD Via Nero.  Since I am new to linux, I don't really know what I am doing when it comes to backing up my DVD's in Ubuntu.  I have, however, acidrip, ogmrip, dvd::rip, and K9Copy at my disposal.  I tried ogm but it gave me an eta of over 3 hours, which i found unacceptable.  Then i tried dvd::rip, which left me with some .rip file and about 7vobs, that I didn't know what the hell to do with.  So that ended there.  Then I tried acid rip, which I thought was quite fast, but the only thing was that the film that I was trying to rip had (forced subtitles) in it.  I didn't click for subtitles, because i didn't want to see an english film with english subtitles, and only want the forced ones in it.  If anyone can help me with a simple way to rip - DVD to AVI, then back to DVD, as quick and as painlessly as possible.  Then I will be a happy man - Thanks In Advance - bipolaric.  P.S This Ubuntu Rocks !!!!-

---

### Post by bipolaric on 2008-07-25
I am trying to rip them to the Hard Drive in AVI format, but hope to ALSO be able to convert the AVI Format BACK to DVD, should I need to, thanks :)

---

### Post by bipolaric on 2008-07-25
I am trying to back-up my star wars DVD to AVI, so I can watch it on my PC.
But I have encountered a problem.  There are subtitle options, but I don't need them, there are however, "forced" subtitles in the film. i.e where the aliens speak.  But when my rip is finished these subtitles are not in the film.  What am I doing Wrong ?  I am using acidrip, because it's fast as hell, and other than this, I see no problem with it.

Thanks - bipolaric

---

### Post by bipolaric on 2008-07-26
DVD to AVI - Subtitle Problem 

I am trying to back-up my star wars DVD to AVI, so I can watch it on my PC.  But I have encountered a problem. There are subtitle options, but I don't need them, there are however, "forced" subtitles in the film. i.e where the aliens speak. But when my rip is finished these subtitles are not in the film. What am I doing Wrong ? I am using acidrip, because it's fast as hell, and other than this, I see no problem with it.

Thanks - bipolaric

---

### Post by bipolaric on 2008-07-26
I am trying to back up my DVD collection to my PC, but I am having a problem with the "forced" subtitle issue.  If no-one can help me I'm going back to XP, because, while I am impressed with my new Ubuntu, it just doesn't seem to work.  I have, acidrip, dvd::rip, ogmrip, and k9copy at my disposal, but just can't get these "forced" subtitles in my film, once it has been ripped.  Saying that I had no problems in doing it with XP.  It's a shame really, this Ubuntu is quite nice.

---

### Post by xc3RnbFO8P on 2008-07-26
Can you show screenshot of K9copy,
the dvd tree?

---

### Post by overdrank on 2008-07-26
To bipolaric please do not make multiple threads on the same issue. I have merged your threads. Threats to return to windows should not be used as many users of the forums use windows. :)

---

### Post by mc4man on 2008-07-26
> I didn't click for subtitles, because i didn't want to see an english film with english subtitles, and only want the forced ones in it Some titles use forced subs which are a separate substream, some used hard coded which are part of the video stream. Star wars uses forced, probably the 2nd english substream.
Once you rip to avi or rip to video_ts with new .ifo's created, the 'forced' stream is no longer forced, you'll have to turn it on manually. (if it's present).
Forced subs are set in an .ifo and also can be affected by chosen audio stream
> Can you show screenshot of K9copy,
the dvd tree?  This is your best bet as most star wars dvds have a slightly different structure. This is due to the opening sequence which is available in 2 or 3 versions based on audio language chosen so you'll probably see the 'movie' title listed  2 or 3 times. (title 1, title 2, title 3 or thereabouts)

---

### Post by linuxisfree on 2008-09-16
Have you tried Acidrip? I find it pretty good.:)

---

### Post by nickie_ferrante on 2008-09-16
If you're willing to just forgo the whole .avi thing and rip your dvds into perfect quality to have a proper backup, then an easy way to do it is to rip the dvds as .vob files, doable with dvd::rip or even just a transfer from the dvd itself, then using the following command to merge them to a single .mpeg file:

cat ~/first_file.vob ~/second file.vob ~/etc > ~/output_filename.mpeg

simply include all of the vob files (in order!) into the command and it'll come into one nice neat little package.

Keep in mind that this is uses one hell of a lot of space, but gives no reduction in quality and takes very little time at all compared to transcoding to .avi

---

### Post by liquidfunk on 2008-09-16
I just insert the disc, and right click Copy Disc to ISO image. Then play it in VLC. Simple. Then you get the whole DVD plus the menu's and extras.

---

