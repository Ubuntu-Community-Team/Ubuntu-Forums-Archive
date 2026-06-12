---
title: "banshee users, how do you deal with duplicates?"
date: 2013-11-16
forum: Multimedia Software
---

### Post by haruX on 2013-11-16
I chose banshee over rhythmbox to sort out my music, but banshee seems to have terrible duplicate management. A same exact song can be added to a same playlist but not filtered out as a dupe.
I sync my music to my device and I want to make sure all my musics are synced inside but the number always don't tally and the root cause is always because of duplicate songs.
It is also troublesome to figure out which song I already have in the playlist so that I wouldn't make another bunch of dupes.

I tried some solutions, like delete the banshee.db and make it scan again. It does its job, but when I import back my old playlists, all the songs are added back as duplicate!!:x:x

banshee 2.6.1

---

### Post by BrunoLotse on 2013-11-17
Hi:) I am running the same 2.6.1 version. Have no problems really... When you execute this command what would you have?```
dpkg -l | grep duplicatesongdetector
```I have this version```
ii  banshee-extension-duplicatesongdetector                     2.4.0-1ubuntu1                               Duplicate song detector extension for Banshee
```Cheers,Bruno

---

### Post by haruX on 2013-11-19
> **BrunoLotse said:**
> Hi:) I am running the same 2.6.1 version. Have no problems really... When you execute this command what would you have?```
dpkg -l | grep duplicatesongdetector
```I have this version```
ii  banshee-extension-duplicatesongdetector                     2.4.0-1ubuntu1                               Duplicate song detector extension for Banshee
```Cheers,Bruno

Hi bruno,

thanks for your help. I've checked that I have the extention just that I didn't activate.

I have a few questions.. is the extention working in the background or i must manually trigger "Detect Duplicate Songs"?

Noticed that it is not very clear cut in the "duplicates" list generated.. it just dumps me with a long list.. is it in the following format?

---SONG1_ORIGINAL----
---SONG1_DUPLICATE---
.....

The auto detector is not very accurate as well :(.. which is why I put quotes over the "duplicates". I've found unique songs being flagged out as duplicate.. I have 2 completely different album also being flagged out as duplicate (if it is indeed in the above format)

---

### Post by BrunoLotse on 2013-11-20
Hi:) I run duplicates detector manually Tools->Detect Duplicate Songs . I do not have many items in Music folder. Mostly in Videos. Thus, there is no duplicates really. As far as your other questions I would suggest visit Banshee forum and raise them there [http://banshee.fm/support/forum/](http://banshee.fm/support/forum/)There should be Banshee developers who'd be able cover everything.Cheers,Bruno

---

### Post by haruX on 2013-11-20
thanks for the response! :)
you are right, I could get better response posting in banshee forums.

appreciate your help in this.

-haru

---

### Post by BrunoLotse on 2013-11-21
Anytime:) Well, the best I could.Cheers,Bruno

---

