---
title: "Programs needed to back up Blue-Ray Movies"
date: 2008-07-01
forum: Multimedia Software
---

### Post by wcunkefe on 2008-07-01
Hi all,
     I would like to catalog all of my blu-ray movies on the hard drive of my ubuntu media server, but am not sure what applications are needed to do so.  What I want to do is this: Insert my blu-ray movie, store a copy of the movie on the hard drive in a format that would allow me to play the movie from the hard drive.  This way I do not have to keep all of my blu-ray disks in the livingroom.  Any help is appreciated... I have been searching forums and google all afternoon without much luck.

Thanks in advance,
     Wayne

---

### Post by aeiah on 2008-07-02
have you tried:
```
dd if=/dev/cdrom of=/film.iso
```

im assuming if your bluray drive is working in linux that its working because you're decrypting to watch (like with dvds) so you should just be able to do that line, like you would with dvds. of course, this doesnt strip all the crap out. are you wanting to strip out the extra languages and features, or is a pure image ok, or are you aiming to convert to 720p or 1080p x264 .mkv?

---

### Post by wcunkefe on 2008-07-06
I have not purchased a bluray drive yet... I am planning to buy a PS3 only if I can store all of my movies in a format that can be accessed by the PS3 OS.  If you could let me know step-by-step how to (once I have the bluray drive and everything functioning) create an image of the movie that could be played (via the network) by the PS3 OS... that would help me out tremendously.  Thanks for your help!

---

### Post by xboxbman on 2008-07-10
> **aeiah said:**
> have you tried:
```
dd if=/dev/cdrom of=/film.iso
```

im assuming if your bluray drive is working in linux that its working because you're decrypting to watch (like with dvds) so you should just be able to do that line, like you would with dvds. of course, this doesnt strip all the crap out. are you wanting to strip out the extra languages and features, or is a pure image ok, or are you aiming to convert to 720p or 1080p x264 .mkv?

i'd like to strip out all the extra stuff and be left with a 720p .mkv, but have no idea how to do this in Ubuntu.  If you know, please share with the class.

---

### Post by cariboo on 2008-07-10
This program [OGMRip]("http://www.videohelp.com/tools/OGMRip"), looks like it will do what you want.

Jim

---

