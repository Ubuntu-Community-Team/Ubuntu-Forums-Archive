---
title: "Capacity of a DVD"
date: 2009-11-19
forum: Multimedia Software
---

### Post by Krupski on 2009-11-19
Hi all,

I always make backups of movies that I buy (no I don't pirate!) :)

Anyway, I've run across a few disks that were marked "DVD" and indeed were readable in a DVD drive (a drive that CANNOT read a Blu-Ray disk).

The strange thing is, the data was not 4.7 gigabytes or 8.5 gigabytes, but TWENTY EIGHT gigabytes!

And these are not "dummy" tracks for copy protection... they are actual .VOB files of 1 gigabyte each and they are playable (they are the various "chapters" of the movie).

So my question is... how the heck do they get 28 gigabytes on a DVD disk???

Is this something new?

Thanks in advance!

-- Roger

---

### Post by lukeiamyourfather on 2009-11-19
Single layer DVD is 4.7GB, dual layer DVD is 9.4GB and there's nothing with more capacity than that for DVD unless its dual sided. Though if it was dual sided you wouldn't be able to see all of the data at once (would have to eject and flip it over).

Sounds like something is funky. Maybe copy protection of some sort, or maybe the disc wasn't produced properly. If you don't mind me asking, what disc is this? Cheers!

---

### Post by mc4man on 2009-11-19
> how the heck do they get 28 gigabytes on a DVD disk???
They don't, it just a form of 'structure protection', probably a ripguard variant, that uses the .ifo's to misrepresent the actual size

I've seen them up to 50 Gb, while in fact the actual content may only be in the 7 Gb range or so.

---

### Post by Krupski on 2009-11-19
> **lukeiamyourfather said:**
> Single layer DVD is 4.7GB, dual layer DVD is 9.4GB and there's nothing with more capacity than that for DVD unless its dual sided. Though if it was dual sided you wouldn't be able to see all of the data at once (would have to eject and flip it over).

Sounds like something is funky. Maybe copy protection of some sort, or maybe the disc wasn't produced properly. If you don't mind me asking, what disc is this? Cheers!

The disk is the new Star Trek movie... and here's the directory listing of "VIDEO_TS":

```

root@storage:/home/shared/dvd-backups/star-trek-new/VIDEO_TS# ls -laF
total 30306196
drwxr-xr-x 2 nobody nogroup       4096 2009-11-18 20:25 ./
drwxr-xr-x 3 nobody nogroup         21 2009-11-18 18:42 ../
-rw-r--r-- 1 nobody nogroup      53248 2009-08-25 21:11 VIDEO_TS.BUP
-rw-r--r-- 1 nobody nogroup      53248 2009-08-25 21:11 VIDEO_TS.IFO
-rw-r--r-- 1 nobody nogroup    2770944 2009-08-25 21:11 VIDEO_TS.VOB
-rw-r--r-- 1 nobody nogroup      14336 2009-08-25 21:11 VTS_01_0.BUP
-rw-r--r-- 1 nobody nogroup      14336 2009-08-25 21:11 VTS_01_0.IFO
-rw-r--r-- 1 nobody nogroup     229376 2009-08-25 21:11 VTS_01_0.VOB
-rw-r--r-- 1 nobody nogroup     411648 2009-08-25 21:11 VTS_01_1.VOB
-rw-r--r-- 1 nobody nogroup      18432 2009-08-25 21:11 VTS_02_0.BUP
-rw-r--r-- 1 nobody nogroup      18432 2009-08-25 21:11 VTS_02_0.IFO
-rw-r--r-- 1 nobody nogroup   20162560 2009-08-25 21:11 VTS_02_0.VOB
-rw-r--r-- 1 nobody nogroup      10240 2009-08-25 21:11 VTS_02_1.VOB
-rw-r--r-- 1 nobody nogroup      38912 2009-08-25 21:11 VTS_03_0.BUP
-rw-r--r-- 1 nobody nogroup      38912 2009-08-25 21:11 VTS_03_0.IFO
-rw-r--r-- 1 nobody nogroup     493568 2009-08-25 21:11 VTS_03_0.VOB
-rw-r--r-- 1 nobody nogroup  302620672 2009-08-25 21:11 VTS_03_1.VOB
-rw-r--r-- 1 nobody nogroup      38912 2009-08-25 21:11 VTS_04_0.BUP
-rw-r--r-- 1 nobody nogroup      38912 2009-08-25 21:11 VTS_04_0.IFO
-rw-r--r-- 1 nobody nogroup     493568 2009-08-25 21:11 VTS_04_0.VOB
-rw-r--r-- 1 nobody nogroup  302620672 2009-08-25 21:11 VTS_04_1.VOB
-rw-r--r-- 1 nobody nogroup      22528 2009-08-25 21:11 VTS_05_0.BUP
-rw-r--r-- 1 nobody nogroup      22528 2009-08-25 21:11 VTS_05_0.IFO
-rw-r--r-- 1 nobody nogroup     493568 2009-08-25 21:11 VTS_05_0.VOB
-rw-r--r-- 1 nobody nogroup  302620672 2009-08-25 21:11 VTS_05_1.VOB
-rw-r--r-- 1 nobody nogroup      20480 2009-08-25 21:11 VTS_06_0.BUP
-rw-r--r-- 1 nobody nogroup      20480 2009-08-25 21:11 VTS_06_0.IFO
-rw-r--r-- 1 nobody nogroup     493568 2009-08-25 21:11 VTS_06_0.VOB
-rw-r--r-- 1 nobody nogroup  302620672 2009-08-25 21:11 VTS_06_1.VOB
-rw-r--r-- 1 nobody nogroup      83968 2009-08-25 21:11 VTS_07_0.BUP
-rw-r--r-- 1 nobody nogroup      83968 2009-08-25 21:11 VTS_07_0.IFO
-rw-r--r-- 1 nobody nogroup  127612928 2009-08-25 21:11 VTS_07_0.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_07_1.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_07_2.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_07_3.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_07_4.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_07_5.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_07_6.VOB
-rw-r--r-- 1 nobody nogroup  134060032 2009-08-25 21:11 VTS_07_7.VOB
-rw-r--r-- 1 nobody nogroup     116736 2009-08-25 21:11 VTS_08_0.BUP
-rw-r--r-- 1 nobody nogroup     116736 2009-08-25 21:11 VTS_08_0.IFO
-rw-r--r-- 1 nobody nogroup  127612928 2009-08-25 21:11 VTS_08_0.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_08_1.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_08_2.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_08_3.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_08_4.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_08_5.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_08_6.VOB
-rw-r--r-- 1 nobody nogroup  134060032 2009-08-25 21:11 VTS_08_7.VOB
-rw-r--r-- 1 nobody nogroup      90112 2009-08-25 21:11 VTS_09_0.BUP
-rw-r--r-- 1 nobody nogroup      90112 2009-08-25 21:11 VTS_09_0.IFO
-rw-r--r-- 1 nobody nogroup  127612928 2009-08-25 21:11 VTS_09_0.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_09_1.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_09_2.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_09_3.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_09_4.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_09_5.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_09_6.VOB
-rw-r--r-- 1 nobody nogroup  134060032 2009-08-25 21:11 VTS_09_7.VOB
-rw-r--r-- 1 nobody nogroup      83968 2009-08-25 21:11 VTS_10_0.BUP
-rw-r--r-- 1 nobody nogroup      83968 2009-08-25 21:11 VTS_10_0.IFO
-rw-r--r-- 1 nobody nogroup  127612928 2009-08-25 21:11 VTS_10_0.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_10_1.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_10_2.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_10_3.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_10_4.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_10_5.VOB
-rw-r--r-- 1 nobody nogroup 1073739776 2009-08-25 21:11 VTS_10_6.VOB
-rw-r--r-- 1 nobody nogroup  134060032 2009-08-25 21:11 VTS_10_7.VOB
-rw-r--r-- 1 nobody nogroup      49152 2009-08-25 21:11 VTS_11_0.BUP
-rw-r--r-- 1 nobody nogroup      49152 2009-08-25 21:11 VTS_11_0.IFO
-rw-r--r-- 1 nobody nogroup  752349184 2009-08-25 21:11 VTS_11_1.VOB
-rw-r--r-- 1 nobody nogroup      26624 2009-08-25 21:11 VTS_12_0.BUP
-rw-r--r-- 1 nobody nogroup      26624 2009-08-25 21:11 VTS_12_0.IFO
-rw-r--r-- 1 nobody nogroup  752349184 2009-08-25 21:11 VTS_12_1.VOB
-rw-r--r-- 1 nobody nogroup      63488 2009-08-25 21:11 VTS_13_0.BUP
-rw-r--r-- 1 nobody nogroup      63488 2009-08-25 21:11 VTS_13_0.IFO
-rw-r--r-- 1 nobody nogroup  752349184 2009-08-25 21:11 VTS_13_1.VOB
-rw-r--r-- 1 nobody nogroup      28672 2009-08-25 21:11 VTS_14_0.BUP
-rw-r--r-- 1 nobody nogroup      28672 2009-08-25 21:11 VTS_14_0.IFO
-rw-r--r-- 1 nobody nogroup  240764928 2009-08-25 21:11 VTS_14_1.VOB
-rw-r--r-- 1 nobody nogroup      16384 2009-08-25 21:11 VTS_15_0.BUP
-rw-r--r-- 1 nobody nogroup      16384 2009-08-25 21:11 VTS_15_0.IFO
-rw-r--r-- 1 nobody nogroup  240764928 2009-08-25 21:11 VTS_15_1.VOB
-rw-r--r-- 1 nobody nogroup      24576 2009-08-25 21:11 VTS_16_0.BUP
-rw-r--r-- 1 nobody nogroup      24576 2009-08-25 21:11 VTS_16_0.IFO
-rw-r--r-- 1 nobody nogroup  240764928 2009-08-25 21:11 VTS_16_1.VOB

```


And note... ALL of those .VOB files are valid data. There's the movie itself, there's the movie in French and there's miscellaneous content like director's comments, scenes from the original 1969 Star Trek series, etc...

The disk itself says right on it "DVD" (not Blu Ray) and it plays in an old DVD burner drive I have (which I _KNOW_ does not read real Blu Ray disks).

What do you think?

---

### Post by stinger30au on 2009-11-19
definately looks like a new copy protection scheme

i bet dvdfab will copy it

---

### Post by mc4man on 2009-11-19
> ALL of those .VOB files are valid data.

They are and they aren't, physically they don't exist.

As posted DVDFab HD Decrypter  running in wine will deal with this or for a linux solution possibly k9copy. ( though for k9 you'd need to probably just do a movie only, no orig. menus. only using the titleset that actually contains the working title

To find the titleset and title of the actual movie vlc should show you.

If k9 can correct the vobu's then you'd be ok.

---

### Post by Krupski on 2009-11-19
> **stinger30au said:**
> definately looks like a new copy protection scheme

i bet dvdfab will copy it

OK I looked carefully at the disk content. A lot of the .VOB files have a 6-some GB size, but a 00:00 "play time" (i.e. they are bogus tracks).

I re-copied *ONLY* the files that had actual play times and the result was about 6.5 GB of data which plays perfectly.

So, my guess is that the huge, but empty files are there to prevent a novice from making a DVD to DVD copy since of course a DVD recordable cannot hold 28 gigabytes!  :)

I missed it at first because I copied the DVD to my Linux file server. There was ample room to hold the bogus files.

Interestingly, I had three different movies in the 28-30 gigabyte size range and they were all:

* New releases
* Produced by "Paramount"

So, now I have to look for (or write) a program that automatically locates the "bogus" files and ignores them while copying the "real" ones.

Again let me point out that I am NOT pirating. I am simply making copies of movies that I purchased so that I can watch them from my file server rather than messing around with a physical disk (which will get scratched up or lost... I've got 3 kids!).

The movies on my file server are the "play" copies and the originals are stored in a closet where they can't get destroyed by the kids.

Oh well... thanks to all for the ideas and info. It indeed appears that this is a "copy protection" scheme... one that works by making the source appear way too large to fit on a DVD.

Thanks again all!  :)

-- Roger

---

### Post by Krupski on 2009-11-19
> **mc4man said:**
> They are and they aren't, physically they don't exist.


You're right... they physically don't exist... but they ARE linked, at least in part, to "real" files since they can be played.

However, when played they are garbage (skipping from scene to scene, switching from English to French, etc...)

I think they are like old MS-DOS "cross-linked" files. The entries are there, and they DO point somewhere, but where they point is random.

Actually, it's clever since at first I tried to "play" each VOB to see if it was "real" and upon seeing a few seconds of video, I assumed that they were good.

But watching a "bogus" VOB for a few minutes reveals that they are just random junk.

They fooled me.

The real trick is to look at the play time field of the file. All the bogus ones are 00:00:00 while "real ones" have a play time (even if it's only 00:00:10 - 10 seconds).

Anything non-zero is "real".

Oh well... I'm sure there's some software out there which already knows how to deal with this "problem". All I need to do is find it!  :)

-- Roger

---

### Post by lisati on 2009-11-19
I haven't come across anything quite like this before and suspect that the copy protection idea has some merit. Perhaps it's set up this way so that if you copy the folder with a simple file-by-file copy without regard to the data structure within and across the files you'll end up using a lot more disk space than is really needed.

---

### Post by Krupski on 2009-11-19
> **lisati said:**
> I haven't come across anything quite like this before and suspect that the copy protection idea has some merit. Perhaps it's set up this way so that if you copy the folder with a simple file-by-file copy without regard to the data structure within and across the files you'll end up using a lot more disk space than is really needed.

Yes... correct.

If someone tries to copy a DVD to a DVD recordable, it will fail since the source will *APPEAR* to be way too large to fit.

Or, the copy program will try so hard to compress the source that the resulting copy will be worse than a worn out VHS tape.

Copying a DVD to a file server will work, but it will waste 20-some gigabytes of space for each disk since only 6 to 8 gigabytes of a 28 to 30 gigabyte copy is "real".

What needs to be done is to have the copy software look at each VOB (chapter) and discard the bogus ones and only copy the "real" ones.

And, that information is probably in the IFO files since, of course, the TV DVD player knows which tracks to play.

Oh well... at least now I understand what's going on.

For a while I was thinking maybe there was some kind of a technology breakthrough..... WOW! 30 gigabytes on a DVD... imagine what that would do on a Blu-Ray disk... 175 gigabytes on a single disk!!!

But alas... it was just an "optical" illusion!  :)

---

### Post by mc4man on 2009-11-19
Ironically I just noticed my son picked up this title the other day.
The 'real' movie is titleset 9 title 21. 

Other than 2 extra's, the menu's and some previews the rest is garbage. A movie only backup would be easy with linux only, a full disk probably not.

(unless you wanted a hdd only copy, then that might be doable

Edit: doing a full disk, hdd only backup now, should only take about 12 min.'s., will test the .iso

---

### Post by mc4man on 2009-11-20
For a simple 'full copy to hdd' see screen. This just copies the disk 'as is', no removal or bypassing of copy or structure protections. An '.iso will playback the same as a disk, ie. the protections are irrelevant, the ifo's provide proper playback info, ect.

( note that this .iso is of no value if wanting to burn a working copy, just for hdd playback.

The unreadable sectors are typical of these style 'ripguard' disks, only a very few. ( by contrast a Sony ARccOS or protectx disks can have ten's of thousands

---

