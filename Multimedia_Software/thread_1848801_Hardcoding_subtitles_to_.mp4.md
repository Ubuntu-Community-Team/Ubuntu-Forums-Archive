---
title: "Hardcoding subtitles to .mp4"
date: 2011-09-23
forum: Multimedia Software
---

### Post by sanseverina on 2011-09-23
[SIZE=2]Hello,

I try to hardcode .srt subtitles to a .mp4 file in Avidemux. I followed the instructions found on different sites but the subs won't appear on the video... I use version 2.5.4. 

I am also interested in other easy ways of hardcoding subs to video files. I would really appreciate a step-by-step guide on how to embed .srt subtitles with mencoder. I've googled for tutorials but I am quite new to Linux and I don't have a grip on these mencoder commands.

Many thanks in advance![/SIZE]

---

### Post by andrew.46 on 2011-09-23
MP4Box will import a few different subtitle formats including .sub, .srt and .idx so this might be worth a go. It is installed with gpac:

```
sudo apt-get install gpac
```

The syntax is:

```
MP4Box -add inputFile destinationFile
```

Hope this helps!

---

### Post by axel206 on 2011-09-24
Check this guide at the avidemux part.

[How to create/edit/embed subtitles in videos using Jubler and Avidemux](http://www.my-guides.net/en/content/view/105/26/)

---

### Post by andoni on 2011-09-24
> **andrew.46 said:**
> MP4Box will import a few different subtitle formats including .sub, .srt and .idx so this might be worth a go. It is installed with gpac:

```
sudo apt-get install gpac
```

The syntax is:

```
MP4Box -add inputFile destinationFile
```

Hope this helps!
That worked! Thanks a lot :D .

---

### Post by andrew.46 on 2011-09-24
> **andoni said:**
> That worked! Thanks a lot :D .

My pleasure :)

---

### Post by shantiq on 2011-09-25
you can also take the mencoder route

> mencoder -sub file.srt -subcp iso-8857-9 -ovc xvid -xvidencopts bitrate=1419 -oac pcm -o file_with_subs.mp4 file.mp4

> mencoder -sub file.srt -subcp iso-8857-9 -ovc xvid -xvidencopts bitrate=1419 -oac copy -o file_with_subs.avi file.avi



of course bitrate up to you...

---

