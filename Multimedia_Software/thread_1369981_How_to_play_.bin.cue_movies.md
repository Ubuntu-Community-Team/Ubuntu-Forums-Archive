---
title: "How to play .bin/.cue movies"
date: 2010-01-01
forum: Multimedia Software
---

### Post by Mr Nemo on 2010-01-01
I have AcetoneIso, but when I mount the .bin or .cue I get an error message that it cannot play that format. Anyway to mount and play these files?

---

### Post by gsmanners on 2010-01-01
A "cue" file stores the layout of a CD and the "bin" file stores the data. That is to say, it is the container for your movie's container.

This will convert the bin/cue files to iso:

```
bchunk movie.bin movie.cue movie
```

At this point you can use something like isomaster to extract the actual movie files.

---

### Post by Mr Nemo on 2010-01-02
I was able to convert the files, but now it wont let me mount, play or extract the files.

---

### Post by shimoda on 2011-07-07
thanks for the tip... worked for me :)

---

### Post by handy on 2011-07-08
I can play .bin/.cue movies with vlc.

You just choose the .bin file & away it goes. :)

---

### Post by rocksockdoc on 2012-01-07
> **Mr Nemo said:**
> I was able to convert the files, but now it wont let me mount, play or extract the files.

> **handy said:**
> I can play .bin/.cue movies with vlc

For me, VLC would not play either the bin nor the cue file ... however, I was able to convert the bin/cue set to an iso and I was able to mount the bin/cue and the iso separately.

Details here:

[LIST]
[*]Desktop Environments: [SOLVED] 			 			[What player or converter do I use to play/convert a 'bin' and 'cue' video file?]("http://ubuntuforums.org/showthread.php?t=1905315"), by rocksockdoc
[/LIST]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210388&stc=1&d=1325930288[/IMG]

---

