---
title: "Convert Bin Cue files to Iso."
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by Melllvar3 on 2007-05-22
How do I convert .Bin and .Cue files to an .ISO image so that I can burn it.

---

### Post by tgm4883 on 2007-05-22
sudo apt-get install bchunk

---

### Post by mitch.c on 2007-05-22
I've never used it, but there's a program called BinChunker for Unix/Linux that does this. It's in the universe repository:
```
$ sudo apt-get install bchunk
```

An alternative might be CDemu (can mount  a bin/cue) to emulate a CD-ROM, and then copy to your physical CD-RW. This is a kernel module you would need to build yourself, so it's a more complex solution.

CDemu homepage: [http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

Cheers.

-- 
Mitch

---

