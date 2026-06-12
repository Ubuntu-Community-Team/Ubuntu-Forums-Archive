---
title: "how do I burn VOB to make a dvd"
date: 2008-09-11
forum: Multimedia Software
---

### Post by tropdoug on 2008-09-11
Hi guys

I am using dvd:rip to rip from a dvd and I want to make a new copy. The rip seems to have gone well. But I have an ifo file, and a couple of logfiles and 4 vob files numbered 001 to 004.

Following another thread on here, I downloaded nero for linux, and tried to add the vob files as instructed to the Video_TS folder. No dice, as it comes up with 'can only accept Video_TS.vob' as the file name. Well I can't name all four of the files the same thing and anything other than the exact name is rejected. 

So I am stuck

Any solutions gratefully accepted

Douglas

PS I tried doing an iso as well, after umount the cdrom, I did ```
dd if=/dev/cdrom of=file.iso bs=1024
```but each time I tried, I came up with "input/output error"0

---

### Post by vanadium on 2008-09-11
If what you have is a valid authored DVD directory structure already, then you can create an iso using
```

mkisofs -dvd-video -o dvd.iso dvd/

```
(where dvd/ is the directory containing your VIDEO_TS and AUDIO_TS folders). The iso can be burned with wathever dvd burning application.

If you only have the VOBs lingering on your disk, then (here I do not have the experience) I think you can author them directly with dvdauthor (or a graphical frontend such as qdvdauthor). dvdauthor will create a video-dvd compliant iso that you can burn.

---

