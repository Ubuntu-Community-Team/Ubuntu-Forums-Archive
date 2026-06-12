---
title: "How do I burn a DVD from these files?"
date: 2009-05-24
forum: Multimedia Software
---

### Post by elcisitiak on 2009-05-24
(Intrepid)

I have a pile of files of the .vob, .bup, .ifo types. I get the feeling I should be able to burn these to a DVD rather easily, but I cannot for the life of me figure out how to. 

I've tried mkisofs

```
$mkisofs -dvd-vido -o filename.iso Folder/
``` 

Where filename is what I want to name the iso file, and Folder is where the (empty) AUDIO_TS, and the EXTRAS_TS and VIDEO_TS folders are. 

My return was

```
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Invalid node - 'Folder/'.
```

I am just completely lost. Can somebody please help me out?

---

