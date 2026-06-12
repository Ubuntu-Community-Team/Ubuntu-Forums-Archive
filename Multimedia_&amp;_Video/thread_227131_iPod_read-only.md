---
title: "iPod read-only"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by dogman24 on 2006-08-01
I have a 5G ipod, and it is being recognised by all my music player programs and File Browser.

There is one problem with linux and my iPod though, it is only read-only, so I can't write any of my music on it. Is there a step by step way I can change the permissions on my iPod so it isnt read-only?

Thanks

---

### Post by lokimon on 2006-08-01
yeah, quite odd, but even if i use a rootshell to set permissions wide open (777) i can't write to the ipod. thought that was weird, too.

---

### Post by jorgesallum on 2008-01-20
The problem is a little bit more complicated. If you want your kernel to be able to read and write in your iPod file system ([HFS]("http://en.wikipedia.org/wiki/HFS_Plus")) you need to set it in your kernel in other to support it or you have to reformat your iPod to another file system (FAT32 for instance). It's amaizing that there is nothing about it in ubuntu-docs (is there?). Have a look on [gnu site about iPod]("http://www.gnu.org/software/gnupod/gnupod.html#SEC6") and [in this forum]("http://www.linuxquestions.org/questions/mandriva-30/ipod-read-only-334942/"). 

I've just looked at the repository (sudo apt-get search hfs) and found it: 
> 
hfsplus - Tools to access HFS+ formatted volumes


So, try it out. "sudo apt-get install hfsplus". :)

JS

---

