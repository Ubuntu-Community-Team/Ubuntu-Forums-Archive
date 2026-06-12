---
title: "Simple Screen Recorder not working for about 3 weeks"
date: 2016-03-25
forum: Multimedia Software
---

### Post by A.O._Stanley on 2016-03-25
Ubuntu 15.10 updated.

Been using SSR for quite some time without issue then it stopped working a few weeks back maybe because of a kernel update. I've been waiting for a fix to show up but none yet.

Anyone else having issues? If so, did you find a solution? 

This is the error message I get when I try to record:

 [COLOR=#ff0000]Muxer::Init] Error: Can't open output file![/COLOR]
 [COLOR=#ff0000][PageRecord::StartOutput] Error: Something went wrong during initialization.


[/COLOR]

---

### Post by sammiev on 2016-03-25
Hi,

You can select advance mode from the grub and select an older kernel to boot from to see if thats the problem.

---

### Post by A.O._Stanley on 2016-03-25
sammiev, 

thanks for the suggestion but no luck.

---

### Post by sammiev on 2016-03-25
I never used the program but thought if it was a kernel issue this may get you around it for now. :(

---

### Post by A.O._Stanley on 2016-04-18
In the screen that shows where I wanted to store the finished file, I just clicked "Browse" and selected my "Video" folder. Apparently this had become corrupted and thus the error. 

Working fine now. And thanks to Maarten Baert for his help on this, as well.

---

