---
title: "Recording file too big, will not play"
date: 2016-07-23
forum: Mythbuntu
---

### Post by alan44 on 2016-07-23
Several times we have found that a program has recorded, but the resulting file is way oversize and will not play, typically 5GB for a 1hr HD program; recordings that play OK are less than 2GB for a 1hr program. This has happened especially when recording episodes of "Scott & Bailey" from WGVU Ch. 35-1, Grand Rapids, MI.

---

### Post by aelfric55 on 2016-07-23
This is not normal behavior whatever the file size. Certainly  5 GB is not particularly large. I normally record entire NFL or MLB games in HD to watch later, where the file size can be 24-30 GB or more and they'll play without any issues. 

There is not much information to go on here. What indications do you have that the 5 GB files are "too large" to be played? Does the frontend crash? Do the files just not open? Are there any clues in the frontend log? Do the files play in some other media player, like MPlayer, VLC, or Kodi, but just not in mythfrontend?

---

### Post by ajgreeny on 2016-07-23
Where are you putting these large files?  Don't forget that you have a file size limit of 4GB if using a fat32 disk.

---

### Post by alan44 on 2016-07-23
> **aelfric55 said:**
> This is not normal behavior whatever the file size. Certainly  5 GB is not particularly large. I normally record entire NFL or MLB games in HD to watch later, where the file size can be 24-30 GB or more and they'll play without any issues. There is not much information to go on here. What indications do you have that the 5 GB files are "too large" to be played? Does the frontend crash? Do the files just not open? Are there any clues in the frontend log? Do the files play in some other media player, like MPlayer, VLC, or Kodi, but just not in mythfrontend?They are "too large" in that they will not play. The "excessive size," I am guessing, is due to some kind of corruption. I've never tried playing them with another player. Sometimes the frontend crashes, sometimes not. The recordings of other episodes of the same series that play OK (also HD) are only about 1.5GB.

---

### Post by aelfric55 on 2016-07-23
> **alan44 said:**
> They are "too large" in that they will not play. The "excessive size," I am guessing, is due to some kind of corruption. I've never tried playing them with another player. Sometimes the frontend crashes, sometimes not. The recordings of other episodes of the same series that play OK (also HD) are only about 1.5GB.

What I was trying to say is that there's no such thing as "too large" here. The software is capable of playing and is expected to play without problem files many times the size of your 5 GB files. Even if you've tried to record these files on a Fat32 disc, they'd have been truncated at 4 GB and these first 4GB should still play. And 5 GB is smallish for an hour of true HD --HD recordings  normally run 5-7+ GB per hour, depending on resolution. Approx. 1+ GB per hour is SD (including widescreen SD) not HD. (Analog comes in the middle at between 2.1 and 2.5 GB per hour.) 

So if these 5 GB files are not playing in mythfrontend, it's not because they're "too large". It must be from another cause. The files could in fact be corrupt from some cause, which is why I suggested trying to play the files in some other player. See if one plays from beginning to end. If the files aren't corrupt, then as I suggested you can check the frontend and backend logs to see whether mythtv is telling you what the problem in playing these uncorrupted files is. It may be something as simple as an incorrect frame index in the HD recording. Or a missing library in the installation.

But in the less likely event that the files themselves are corrupted, then it will be necessary to determine why your recording card is putting down a corrupted mpeg file, or why the file may not be being stored correctly by the hard disc. These kinds of problems are likely to have triggered errors in the backend log at the time the program was being recorded.

---

### Post by alan44 on 2016-08-30
I reinstalled Mythbuntu 14.04.2 from scratch after saving the recordings to an external drive, and I have tried playing them back on my Debian desktop. Some play OK (including some of 11GB or so), some show just a blank white screen, while others display a black screen with an error message, and I was able to click "OK" and exit from it; one displayed a black screen with no error message, and the machine was unusable until I rebooted; most of those had normal file sizes. Strangely enough, I also found recordings from two or more years ago that had long ago been "deleted" from the "View Recordings" listing.

---

