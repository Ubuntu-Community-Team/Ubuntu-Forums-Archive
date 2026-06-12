---
title: "2 questions"
date: 2009-03-16
forum: Multimedia Software
---

### Post by uttaran on 2009-03-16
1) Whenever i run Rhythmbox it uses 30% of my cpu(2.24Ghz.).I've disabled all visualizations,etc.How to reduce this?
2) How to run .dat files in Ubuntu 8.10?

---

### Post by Penguin Guy on 2009-03-16
> **uttaran said:**
> 1) Whenever i run Rhythmbox it uses 30% of my cpu(2.24Ghz.).I've disabled all visualizations,etc.How to reduce this?
2) How to run .dat files in Ubuntu 8.10?
Get a new music player? - Just have a look around for a less CPU-intensive one.

---

### Post by Simian Man on 2009-03-16
> **uttaran said:**
> 1) Whenever i run Rhythmbox it uses 30% of my cpu(2.24Ghz.).I've disabled all visualizations,etc.How to reduce this?

It really shouldn't.  What processor do you have?  Try some other music players.

> **uttaran said:**
> 2) How to run .dat files in Ubuntu 8.10?

".dat" is a common extension for generic data.  So we need a lot more info on what you are talking about here.  What are the files you are referring to?

---

### Post by uttaran on 2009-03-17
Name any player please.
.dat means video files.
1 more problem i'm having...i can't copy any vcd from cd to hard disk.It says 'Input-output' error.I can copy it freely in XP.

---

### Post by 3rdalbum on 2009-03-17
> **uttaran said:**
> Name any player please.

Exaile, Quod Libet, Banshee, Amarok, Juk... do a search in Synaptic Package Manager for "music player" and you'll find a bunch.

> .dat means video files.
1 more problem i'm having...i can't copy any vcd from cd to hard disk.It says 'Input-output' error.I can copy it freely in XP.

Ahh, you should have told us that you meant ".dat" files from VCD. Most people here have never seen a VCD and that's why they didn't know what you meant by ".dat" files.

Windows is the only operating system that can read VCD files without a dedicated player; all other operating systems will not be able to actually read the data on their own. I think it's some form of archaic DRM.

I have an extracted VCD on my hard disk right now; I must have done it in Linux, but I can't remember what I did. Reason tells me that Mplayer should be capable of ripping VCD tracks with something like this:

```
mplayer vcd://1 -dvd-device /dev/scd0  -v -v -dumpstream -dumpfile "/home/chris/vcd_track_1.mpg"
```

No idea if it works though - I don't have VCDs anymore.

---

### Post by uttaran on 2009-03-17
u mean i can't copy any .dat video file!!??It's horrible since most of our video files r in .dat format.
Can u tell me how to automount NTFS drives during startup?It could b done in Gutsy...but what about Intrepid?

---

