---
title: "Can I edit the properties of a set of files with Rhythmbox?"
date: 2015-04-28
forum: Multimedia Software
---

### Post by remmas-sido on 2015-04-28
Hello guys 
I like to convert audio files to m4a format a lot. This is mainly because I like to preserve as much space as possible on my SD card. The problem is that sometimes when you convert audio files from one format to another it became anonymous by that I mean that if the mp3 files were tagged after the conservation they became untagged. I tried to edit the properties of one file a long time ago, but it was unsuccessful. So what can I do?
OS: Ubuntu 12.04 Rhythm-box version 2.96

---

### Post by ajgreeny on 2015-04-28
I have just tried this with a tagged mp3 file which I had just tagged using audio-tag-tool, and converted it to m4a using ```
avconv -i filename.mp3 filename.m4a
``` and the tags were carried over.  You don't say how you have converted filetypes but perhaps you need to use avconv to convert your files if their tags are not carried over.

I do not know if this works for all tagged filetypes converted with avconv, but for mp3 to m4a it appears to work perfectly.

---

