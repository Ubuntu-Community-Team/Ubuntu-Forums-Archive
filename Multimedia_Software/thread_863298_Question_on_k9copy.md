---
title: "Question on k9copy"
date: 2008-07-18
forum: Multimedia Software
---

### Post by CNLiberal on 2008-07-18
I'm trying to switch over to completely ubuntu for my computing needs.  I have a large DVD collection and am attempting to rip them all to ISO (full size, not compressed) and store them on my 2TB MDADM soft RAID5 array.  I started by using k9copy but then moved back to my WinBlowz box and DVD Shrink because I was getting a strange result from k9copy.  It seemed to rip the movie OK, but when I watched it, I noticed that most times on a scene change, I would get the start frame of the new scene, then one of the last frames of the old scene, then the rest of the new scene would follow.  This seemed to happen on most scene changes.  I'll be looking around the net a little more for an answer to this, but thought I'd come here to see if anyone else has seen this issue.  I've seen it on Cars, Live Free or Die Hard, Ocean's Thirteen and Transformers.  I haven't gotten to any older movies yet, but I will soon.  I was thinking it might have to do with the copy protection on these discs, but wanted to check with the community to see what they have seen.  Thanks for your help!

Jim

---

### Post by mc4man on 2008-07-18
Possibly due to the structure protection. Some people might use dvdfab hd.... in wine, but I think it also can have problems with 'easy' structure protections. 
Usually i'll use a modified vobcopy to rip to video_ts and if there was structure protection, repair as needed. I gotta go so can't explain that method and it's occasional limitations. (let me know if interested)
If you know how to use wine and your k9 rips are in file format (video_ts) you could probably fix the dvd structure by doing a full vob scan and then a mock strip with vobblanker, if k9 didn't butcher too badly.
If interested in above let me know and tonight I'll post more concise info

---

### Post by mocha on 2008-07-18
I never had a problem with k9copy, so it probably is issues with those particular movies.  You can use DVDshrink and DVDfab within Ubuntu using Wine if you like.

---

### Post by CNLiberal on 2008-07-18
I have used DVD Shrink on some of these movies under WINE.  It had problems with LFODH (but then again, so did I when I saw how they butchered the franchise).  I believe DVD Shrink died.  Are there any other tools I could use to do this in linux?  What about VLC?  I've read about some streaming and dumping to file, but it doesn't appear to support ISO.  I'd like the ISO option in case I want to burn the file to a DL DVD for backup purposes.  Thanks!

mc4man:

I'd love to hear any ideas you have.  Thanks!

Jim

---

### Post by mc4man on 2008-07-18
I have 2 of the titles you mentioned, transformers and LF&DH. To make any absolutely relevant comments you'd need to be the same region as me (R1).
The big boys tend to treat those in R2 and R4 more harshly those those in R1 in terms of structure protection. (and probably in other ways too)


edit: I can comment I believe on LF&DH
That title has 2 versions- -PG-13 and unrated. There aren't actually 2 separate versions, they are what's called Interleaved. Simply put there is one movie and at certain points it 'jumps' to the add. unrated material and then returns. ( rarely the other way around, a trace in pgcedit would tell, doesn't matter)
Clearly k9copy isn't dealing with this very well.
I'll give vobcopy a try, should to better (just a straight up copy to video_ts)
There is no structure protection on R1 so a basic install of vobcopy would be fine. 
Good command to use (assumes disk is mounted at /media/cdrom0, if different append comm. with <space>/mountpoint
```
vobcopy -v -m -F 16
```

---

### Post by CNLiberal on 2008-07-27
OK.  I used the command that you recommended.  It appears to have worked successfully.  I have a VIDEO_TS folder in my home dir.  What do I do next?  Thanks!


BTW:  I am in Region 1 like u.

Joltman

---

### Post by mc4man on 2008-07-27
> What do I do next?
> rip them all to ISO (full size, not compressed) and store them on my 2TB...
If this is still the case then there's no difference whether it's stored as an .iso or a folder in terms of access or playback. (the only difference is an .iso is accessed as a file, the folder as a directory)

Personally I never use any linux app to create dvd compliant .iso's, mainly because I'm going to burn them to disk and I just don't trust they'll do a proper job (especially with dual layer burns)

I always use Imgburn running in wine to create .iso's and burn, it's never fails other than rare case of bad media
So that's what I'd use to turn the VIDEO_TS into an iso., if you use a linux app just make sure it doesn't 'process' it, just convert to a proper dvd structured .iso.


edit I'll ck. out tranformers later and see if there's anything unusual

You really should try playing back the first before anything and see if the playback is smooth, choose the unrated ver.. If you still have glitches it's the player not the rip. (vlc plays it fine here)


Edit;  tried k9 on  trans..  don't really see any issues, there are a few things that could use cleaning up, but overall k9 did fine. Rip size of k9 = 7720mb, cleaned = 7662mb. There was nothing intentionally mis structured, probably just some sloppy authoring.
(you have set the target size in k9 to  7.8 - 8 gb. so it doesn't process ?)

---

