---
title: "Ripping ARccOS from the command line"
date: 2017-09-04
forum: Multimedia Software
---

### Post by john3voltas on 2017-09-04
Hello.
I've been here: ```
https://ubuntuforums.org/showthread.php?t=1885267
```
Found it interesting but didn't solve my problem.

I want to convert from DVD to MKV with x264/AAC with chapters and subtitles.
Usually (on windoze) I would rip to IFO/VOB, I would take the IFO and load it on PgcDemux, that would extract an M2V, several AC3, chapter text files and SUP files for all subtitles.
From there I would reencode video and audio and use MergeMKV to containerize video+audio+subs+chapters. Easy.
On linux I can use ddrescue to extract a DVD to an ISO file, without the bad sectors. I can then use dvdbackup to break CSS and extract a single title or a full titleset.
But then I don't know what to do with it.
Why? Because dvdbackup either only gives me a set of VOB files (-t #title_to_extract) or it gives me a set of VOB files with an IFO (-T #titleset_to_extract). Using "Main Movie" (-M) doesn't work on most DVD's.
So, -t gives me just the group of cells belonging to the the movie but no IFO.
Then -T gives me several group of cells (not just from the movie) with the IFO.
None gives me just the cells for the movie with the IFO.
Besides, even if I get the IFO, what do I do then? I don't know a Linux tool such as PgcDemux to demux the tracks...
Any hel will be greatly appreciated.
Cheers

---

### Post by mc4man on 2017-09-04
Years ago when I fooled around  with dvd's a lot I sometimes used ubuntu to fix *some* structure protected disc's. 
(- more for the challenge than anything useful as I always had windows around..
To do some of the required work I used VobBlanker & PgcEdit running thru wine (PgcEdit had a linux version but the interface was poor.. Also at some point PgcEdit went to a paid version but the older free ones worked fine for this stuff.

So possibly if it's PgcDemux you need it may also run thru wine.

It's also possible handbrake can deal with this, it always claimed to do ArccOS but back then ArccOS was mainly just tons of unreadable sectors & maybe a 'misdirected' navigation or 2..

---

### Post by john3voltas on 2017-09-05
So, no native Linux tools to play around with IFO's?
If not, then what would be my best approach with HandBrake in order to make a MKV with x264 video, AAC audio, chapters taken from the DVD and Subtitles?
I'm asking because after ripping with dvdbackup, I try to feed HandBrake with the VOB's that I got from dvdbackup but it appears to only read the first VOB.
Even if I set dvdbackup to rip to a single VOB, then it gets all very confusing with the audio and subtitles language because without the IFO it can't tell which track is English or French, etc...
And I woudn't like to rely on HandBrakeCLI to rip directly from DVD because someone at their IRC channel told me their ripping capabilities were not to be relied upon.
I feel confused. Probably because everybody is ripping with windoze tools through wine or with DVDFab for Ubuntu, but those are GUI, not CLI...

---

