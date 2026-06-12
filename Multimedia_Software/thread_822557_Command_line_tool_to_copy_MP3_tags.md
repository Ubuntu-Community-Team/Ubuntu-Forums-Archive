---
title: "Command line tool to copy MP3 tags"
date: 2008-06-08
forum: Multimedia Software
---

### Post by mia.king on 2008-06-08
Hi, 
I frequently resample my voice mp3 files to smaller sizes. I'm trying to automate/bash, copying across the id2/3 tags to the new file.

lame -mp3input $1.mp3 $1_small.mp3 .......

i've looked at
easytag
id3tools

but they don't seem to provide the this functionality

tag -source 1stfile.mp3 -copyto 2ndfile.mp3

Thanks for any suggestions.

---

