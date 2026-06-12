---
title: "How do you merge two recordings?"
date: 2009-11-22
forum: Mythbuntu
---

### Post by cabbage on 2009-11-22
Hi,

I've recorded something which has a news break in the middle. This means I have two separate recordings for the same film.

Is it possible to merge these so that I've only one entry in the recordings list?


Thanks,

Cabbage.

---

### Post by pjw1965 on 2009-11-22
Hi

If both films are on the same channel just after eatch other:
- Just record the one and change the end time to match both recordings.

Or 
- export both recordings (I export to divx-avi) and merge with avimerge avidemux or other tools

And yes, I'd also like to merge inside myth, in the edit mode for example.

---

### Post by ian dobson on 2009-11-22
Hi,

Merging within mythtv wouldn't be that easy, MythTV records the exact position (bytes from start of file) for exact searching/frame exact jumping within a file (this lands in the recordedseek table). As well as commercial skipping. 

Combining 2 recordings to one would involve copying the 2 files into one, then combining the recordedseek table entries so that the entries in the seek table for the second file recorded are stored using the end point of the first file as an offset.

I know I had a look at doing this and gave up, programing was not the problem, more the seek table just didn't want to work correctly. Maybe one day I'll have a look at it again.

Regards
Ian Dobson

---

### Post by cabbage on 2009-11-23
Thanks for the comments. I kinda guessed that I'll need to export and then merge.

Just downloaded nuvexport only to find I need to rebuild ffmpeg to get divx support.

Are there any .debs of this around?

---

D'oh - just found this thread:

    [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by cabbage on 2009-11-26
OK... this is really easy. Just edit the movies and do a lossless transcode to cut the bits out within Mythtv.

Then do:

    mencoder -ovc copy -oac copy file1.mpg file2.mpg -o file.avi

Only takes a few minutes - no long transcoding..!

---

