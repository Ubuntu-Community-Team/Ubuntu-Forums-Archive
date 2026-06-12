---
title: "From Topfield to DVD"
date: 2009-06-09
forum: Multimedia Software
---

### Post by physwizz on 2009-06-09
I've been working on a process to create a DVD from a movie recorded on the topfield using Ubuntu 8.10

From Topfield PVR to DVD

1. Copy file from topfield using "puppy"
[INDENT]     *puppy -c get 'DataFiles\filename.rec' 'filename.rec'*
[/INDENT] 2. Use "Project X" to cut out ads and demux
[INDENT]     results in 2 or 3 files **filename.m2v filename.ac3 filename.mp2**
[/INDENT] 3. Use mplex1.exe to form mpg file
[INDENT]     *wine mplex1.exe filename.m2v filename.ac3 filename.mpg*
[/INDENT][INDENT]         or
    *wine mplex1.exe filename.m2v filename.mp2 filename.mpg*
[/INDENT] 4. Use DeVeDe to create iso file
[INDENT]     click on "adjust disc usage" to make it to size
[/INDENT] 5. Right click on iso file
[INDENT]     select "Write to disc"
[/INDENT] 

If anyone has found a better way I'd be interested to try it.

---

