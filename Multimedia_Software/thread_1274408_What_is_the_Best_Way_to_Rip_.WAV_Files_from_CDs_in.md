---
title: "What is the Best Way to Rip .WAV Files from CDs in Ubuntu?"
date: 2009-09-24
forum: Multimedia Software
---

### Post by Groucho Marxist on 2009-09-24
I just read through our forum's [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") and only came across articles about converting compressed audio from one format to another compressed audio format. However, I have not found an article yet that explains how I can rip uncompressed WAV files from a CD. Due to the switch to HD-Radio this year, compressed audio files will sound horrible when played over all-digital airwaves. My reasoning for mentioning this is because I am doing audio pre-production research for my job, as I work as an on-air personality for my college radio station. My sincerest thanks to anyone here who can help answer this question :)

---

### Post by NewlyHuman on 2009-09-24
You can't get an exact copy of the original audio off the CD, because it's not written as data, but as a stream. For the best results, you'll want to use something with error correction, such as Rubyripper (which makes use of cdparanoia).

I wouldn't use WAV, as uncompressed audio is a bear to store in bulk. FLAC should do fine, lossless compression of around 50% usually. Additionally, I doubt lossy-sourced audio will be noticeable to listeners - HD Radio bandwidth is still far less than CDDA, or even FLAC. While processing a lossy-sourced signal is less than ideal, it's almost assuredly unnoticeable to most listeners.

From my indirect experience with college radio, plenty of programming is sourced from 192 kbit MP3s on iPods.

---

### Post by ron999 on 2009-09-24
@Groucho Marxist
Hi
Sound Juicer will do the job.
Also K3b has a 'Create Audio CD' option, use Copy CD > Only create image.
Look for these two programs in the Ubuntu repository.

---

### Post by andrew.46 on 2009-09-24
Hi Groucho Marxist,

The script abcde will do this. The easiest way would be to simply run it as:

```
abcde -o wav
```

and let the defaults do the dirty work for you! Or you can extend the commandline as you wish or write up a series of commands in a $HOME/.abcde.conf file.

Andrew

---

### Post by NewlyHuman on 2009-09-24
> **ron999 said:**
> @Groucho Marxist
Hi
Sound Juicer will do the job.
Also K3b has a 'Create Audio CD' option, use Copy CD > Only create image.
Look for these two programs in the Ubuntu repository.

Sound Juicer is decent in that it uses cdparanoia, but Rubyripper's rips are of verifiably better quality, as it rips each track multiple times and checks for inconsistencies.

I'd avoid K3b. It doesn't do any error checking, and thus the audio sourced from its rips is questionable, as are the images it produces.

---

### Post by mc4man on 2009-09-24
I would also say give rubyripper a try, maybe have it rip to .wav and .flac and see what suits you. ( or try all the possible formats, rr is very easily configured to rip using any valid parameters for pretty much any foramt, I have it use NeroAac with atomic parsley tagging

While you used to have to build there's apparently a ppa now, see here

[http://ubuntuforums.org/showthread.php?t=799621&page=9](http://ubuntuforums.org/showthread.php?t=799621&page=9) (post 82

Or if you don't wish a ppa then I put up an all.deb for hardy thru karmic here 
( though I may pull and patch for auto-ripping in the background - then  again maybe not, not sure there's much interest in that 

[http://ubuntuforums.org/showpost.php?p=7909514&postcount=17](http://ubuntuforums.org/showpost.php?p=7909514&postcount=17)

---

### Post by markharding557 on 2009-09-25
ripperx is good

---

### Post by andrew.46 on 2009-10-09
Hmmmm.... I suggested abcde which might very well have been a little silly. Most people will be using abcde with cdparanoia to rip the cds to wav format so I suspect it would actually make more sense to use cdparanoia *directly* on the commandline. Lots of options there as well as well as some pretty crazy 'output smilies'!

Andrew

---

