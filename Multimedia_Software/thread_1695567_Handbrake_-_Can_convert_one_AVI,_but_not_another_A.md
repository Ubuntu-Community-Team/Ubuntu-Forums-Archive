---
title: "Handbrake - Can convert one AVI, but not another AVI. What?"
date: 2011-02-26
forum: Multimedia Software
---

### Post by Roasted on 2011-02-26
I have a few live concerts in AVI format I wanted to convert to mp4 since that is the only video format the Google CR-48 currently sort-of supports. I can successfully convert a series of AVI TV shows, including a Pink Floyd concert in AVI. But if I turn around and try to convert a Pearl Jam convert in AVI format, it instantly says RIP DONE! with a 1.5kb file from the convert in the destination folder.

Not too sure what else to do??

---

### Post by inobe on 2011-02-26
right click file and hit properties, what's the file size and properties?

sounds like a corrupt file.

---

### Post by Roasted on 2011-02-26
> **inobe said:**
> right click file and hit properties, what's the file size and properties?

sounds like a corrupt file.

I won't be at my desktop till Monday, but I really don't believe they are corrupt, as there are two particular Pearl Jam AVI's that do this. Part 1 and Part 2 of the concert.

---

### Post by inobe on 2011-02-26
when i stated being corrupted, i meant by some sort of DRM?

give this a try, simply cd to the directory containing the file and comment out **marked in bold** to replace with actual file names, start must be actual file name, the end can be any name.

```
ffmpeg -i **start**.avi -s 720X480 -sameq -ar 44100 -ab 192 **end**.mp4
```

---

### Post by emptythevoid on 2011-03-01
Could also give WinFF a shot.

---

### Post by JohnAStebbins on 2011-03-02
> **Roasted said:**
> I have a few live concerts in AVI format I wanted to convert to mp4 since that is the only video format the Google CR-48 currently sort-of supports. I can successfully convert a series of AVI TV shows, including a Pink Floyd concert in AVI. But if I turn around and try to convert a Pearl Jam convert in AVI format, it instantly says RIP DONE! with a 1.5kb file from the convert in the destination folder.

Not too sure what else to do??

It is also helpful to look at the encoding log HandBrake generates.  It creates a log for every encode you do and stores them in ~/.config/ghb/EncodeLogs directory.  If you don't understand the log, try posting in the the handbrake support forums.  Someone might be able to help you there.
[http://forum.handbrake.fr/](http://forum.handbrake.fr/)

---

