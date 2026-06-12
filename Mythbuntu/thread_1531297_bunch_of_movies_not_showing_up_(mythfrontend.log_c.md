---
title: "bunch of movies not showing up (mythfrontend.log clue?)"
date: 2010-07-14
forum: Mythbuntu
---

### Post by usererror on 2010-07-14
this is probably going to sound very strange.

I have about 70 videos that are not ripped but on DVDs.

There are "place holders" in /var/lib/mythtv/videos that are a 4.0MB video I made that represent all 70 of these videos.  They are all named "movietitle.avi" 

But about 20 of them do not show up when I do scan for changes in MythVideo.

In mythfrontend.log I see the following line for about 20 videos, but some still show up, but some do not:

```

2010-07-14 20:42:14.399 Hash d8b3f299f18f626c already exists in the database, updating record 3066 with new filename Movies/40 Year Old Virgin.avi
```

Is this because the 70 files are all identical except for the file name?  Why do some show up fine from the scan and the others do not.

All are same owner, group and permissions.

Thanks!!

The 4.0 MB file is basically a quick video with text that I made with one of the linux video editors that just has the mythtv background that says "get DVD from DVD Rack in basement"

---

### Post by nickrout on 2010-07-16
mythvideo now hashes all videos so it can tell when you change a file name or move a file to another directory. This means that your identical files are seen as the same movie, despite having different names.

Not sure how these files interact with your system. Maybe change some of the metadata in the avi files, even a change of one byte in the file will produce a different hash.

---

### Post by usererror on 2010-07-16
Thanks! That fixed the issue.  I went through and added the movie title to the Metadata for each one that the mythfrontend log was showing a problem with.

I used this command:

```
mencoder -ovc copy -oac copy SourceFile.avi -info name="Video Title" -info comment="File Title Created with Mencoder Info tag "  -o OutputFile.avi
```

That was from this post: [http://ubuntuforums.org/showpost.php?p=8031373&postcount=5](http://ubuntuforums.org/showpost.php?p=8031373&postcount=5)

It is worth noting that for file names that contain **spaces** the output file could not contain spaces also for some reason.  Only the source file using "File Name With Spaces.avi" format would work.  Even using quotes with the output file name would not work for me.

Regardless the duplicate hashes were the issue, adding the metadata helped Myth see the differences.

---

