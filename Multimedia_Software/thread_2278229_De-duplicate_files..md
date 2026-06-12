---
title: "De-duplicate files."
date: 2015-05-14
forum: Multimedia Software
---

### Post by 1clue on 2015-05-14
Hi,

Trying to de-duplicate files.  I need recommendations on software and technique to do this.

In a large part these are multimedia files:
[LIST=1]
[*]Music scanned from my CD collection
[LIST=1]
[*]Yes, I'm an old guy.  I have never bought or downloaded music online, all this comes from physical CDs.  I have all the originals in boxes in my basement.
[*]There are thousands of songs, not counting duplicates.  This is just from looking at the stacks of boxes of music in my basement.
[*]Some of this is duplicated through syncing between the phone and the computer, and I've found as many as 10 copies of some songs.
[LIST=1]
[*]some_band_some_song
[*]some_band_some_song-2
[*]some_band_some_song-3
[*]some_other_name_for_the_same_song
[*]some_other_bitrate_for_the_same_song
[/LIST]

[*]They were all pulled from a CD directly, which in my understanding means the files may not be binary identical.
[*]Some songs are at a higher bitrate than the others.  I want the higher bitrate song.
[/LIST]

[*]Pictures and video from phones and cameras.
[*]There are no copyrighted videos involved.
[/LIST]

So here's what I want:
[LIST=1]
[*]Music:
[LIST=1]
[*]I'd like to de-duplicate songs first to remove all binary identical files, WITHOUT a hard link or symbolic link.  Just get rid of them.
[*]Re-scan, if possible, to remove inferior bitrate songs where there are better quality versions.
[*]I'd then like to standardize the names on artist/album/track-song or something like that, but not really sure how to at this point.
[/LIST]

[*]Pictures:
[LIST=1]
[*]de-duplicated based on binary content, and moved to an organized place (folders) based on original date/time of the oldest copy.
[*]There is very little cropping/editing of video or pictures, and if any of that happens I want to keep both pieces.
[/LIST]

[*]Other files:
[LIST=1]
[*]I guess these are going to be a lot like pictures in terms of process.
[/LIST]
[/LIST]

I found this link, but not sure how good it is:  [http://xmodulo.com/dupeguru-deduplicate-files-linux.html](http://xmodulo.com/dupeguru-deduplicate-files-linux.html)

---

### Post by speartip on 2015-05-15
There is a program in the repos called rdfind. I have never used it, but it might be what you're looking for.

---

