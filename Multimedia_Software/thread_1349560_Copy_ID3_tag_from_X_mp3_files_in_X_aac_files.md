---
title: "Copy ID3 tag from X mp3 files in X aac files"
date: 2009-12-08
forum: Multimedia Software
---

### Post by flapane on 2009-12-08
Let's say I have a mp3 128kbps music collection.
Now I ripped all these files from my cd's in aac with higer bitrate.
I was wondering if there was any way to batch copy ALL my mp3 id3tag into my new m4a files, assuming they will have the same name but different extension.
I think that the script should feature an id3 reader and a mp4 tag writer and... something else.
Any bash geek? :)

---

### Post by flapane on 2009-12-09
Done it
[http://pastebin.com/f37c307c8](http://pastebin.com/f37c307c8)[URL="http://pastebin.com/dd8427e6"]
[/URL]

---

### Post by flapane on 2010-01-06
I have a problem:
It seems that all the mp4 tagged files have a leading space at the beginning of every tag:
```
 mp4info Craig\ David\ -\ Walking\ away.m4a 
mp4info version 1.6
Craig David - Walking away.m4a:
Track    Type    Info
1    audio    alac, 204.892 secs, 1011 kbps, 44100 Hz
 Name:  Walking away
 Artist:  Craig David
 Writer:  Craig David/M. Rosena Hill
 Year:  2000
 Album:  Born to Do It
 Track: 7 of 14
 Disk: 1 of 1
 Genre: Rock
 Grouping:  Craig David
 Comment:  Warner Bros.
 Cover Art pieces: 1
 Album Artist: Craig David

```It should be 
```
Name: Walking away
and not
Name:   Walking away
```However it sounds strange, because if I output the script just BEFORE tagging the mp4 files, there isn't any leading space.

id3 mp3 OUTPUT:
```
Walking away
Craig David
Born to Do It
2000
Rock
7
Craig David
Craig David/M. Rosena Hill
Warner Bros.

```

---

