---
title: "dvdrip cluster: avi file no video data"
date: 2008-06-05
forum: Multimedia Software
---

### Post by LuisLlana on 2008-06-05
Hello,
  I have been trying to set a dvdrip cluster at home. I have been trying to set two nodes unseccesfully. So I have decided to check just one node and I have the same problem: when it has to merge all the chunks I receive this error:
```
Thu Jun  5 18:58:23 2008 [1] El trabajo 'Incorporar partes de video - título #1, PSU #2' salió con el error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/multimedia/imagenes/dvdrip/cars/avi/001/audio-video-psu' && `which nice` -n 19 execflow avimerge -i /multimedia/imagenes/dvdrip/cars/avi/001/chunks-psu-02/* -o /multimedia/imagenes/dvdrip/cars/avi/001/audio-video-psu/cars-001-av-psu-02.avi  -p /multimedia/imagenes/dvdrip/cars/avi/001/audio-psu-02/cars-001-audio-psu-02-00.avi  && rm /multimedia/imagenes/dvdrip/cars/avi/001/chunks-psu-02/* '/multimedia/imagenes/dvdrip/cars/avi/001/audio-psu-02/cars-001-audio-psu-02-00.avi' && echo EXECFLOW_OK

Output: AVI open: avilib - AVI file has no video data

```

Luis.

---

### Post by fujikofujio on 2008-12-11
> **LuisLlana said:**
> Hello,
  I have been trying to set a dvdrip cluster at home. I have been trying to set two nodes unseccesfully. So I have decided to check just one node and I have the same problem: when it has to merge all the chunks I receive this error:
```
Thu Jun  5 18:58:23 2008 [1] El trabajo 'Incorporar partes de video - título #1, PSU #2' salió con el error: Command exits with failure code:
Command: umask 0002; mkdir -m 0775 -p '/multimedia/imagenes/dvdrip/cars/avi/001/audio-video-psu' && `which nice` -n 19 execflow avimerge -i /multimedia/imagenes/dvdrip/cars/avi/001/chunks-psu-02/* -o /multimedia/imagenes/dvdrip/cars/avi/001/audio-video-psu/cars-001-av-psu-02.avi  -p /multimedia/imagenes/dvdrip/cars/avi/001/audio-psu-02/cars-001-audio-psu-02-00.avi  && rm /multimedia/imagenes/dvdrip/cars/avi/001/chunks-psu-02/* '/multimedia/imagenes/dvdrip/cars/avi/001/audio-psu-02/cars-001-audio-psu-02-00.avi' && echo EXECFLOW_OK

Output: AVI open: avilib - AVI file has no video data

```

Luis.

you and I are on the same boat! getting so frustrated with lack of info regarding this problem.

---

### Post by wdconinc on 2009-01-02
I am having the same problem ("AVI file has no video data" on a cluster).  In my case the PSUs for which it complains do not actually contain any data (avi sizes of only a couple of kb).  All of the video and audio data is contained in the other PSUs.  The work-around for my problem was therefore just to do some manual avimerge'ing of the remaining PSUs, and of the PSUs in avi/<chapter>/audio-video-psu.  This created a perfectly fine avi of the entire dvd.

---

### Post by LuisLlana on 2009-05-22
I presume that my problem is the same. Please can you explicit the workaround? I do not know how to do it

---

