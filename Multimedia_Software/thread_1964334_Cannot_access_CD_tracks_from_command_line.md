---
title: "Cannot access CD tracks from command line"
date: 2012-04-23
forum: Multimedia Software
---

### Post by jbarjoy on 2012-04-23
In Ubuntu 10.04 I played CDs from the command line, using gvfs. This was useful in many ways. I discovered that a CD in the drive caused a subdirectory to be created under ~/.gvfs, named "cdda mount on sr0/".  So I created a symbolic link to this directory named "CD", and then I could address the cd contents as "CD/Track N.wav", and a series of tracks as "CD/Track {M..N}.wav".  I could play, rip, or modify using SoX.  Best of all, I could precede the PLAY command with a SLEEP, allowing me to go into the next room where my good speakers were placed before the music started.

But not so in Ubuntu 11.10.  When a cd goes into the drive, nothing appears under the .gvfs directory.  I have read everything I could find about gvfs.  The documentation is very skimpy, and sometimes self-contradictory.  I have tried using gvfs-mount, even gvfs-mkdir, but these attempts are guesswork, so I am not giving you the error messages at this time -- I don't even know if my commands make sense.

Can someone show me the correct way to access cd tracks as files on the command line in Ubuntu 11.10?  I don't know whether the gvfs system is broken or has changed.  My version of Ubuntu was bought with a magazine, so who knows if it was complete and accurate!

---

### Post by andrew.46 on 2012-05-03
> **jbarjoy said:**
> Can someone show me the correct way to access cd tracks as files on the command line in Ubuntu 11.10? 

I don't know about 'correct' but MPlayer might be one option for you:

```
mplayer -cache 2048 -cache-min 80 cddb://
```

There are many variations for this commandline but this is the basic one...

---

