---
title: "video in gtkpod problem"
date: 2011-11-03
forum: Multimedia Software
---

### Post by tommah04 on 2011-11-03
Hey all,

I've been trying like the dickens to get video onto my ipod and the closest I got was using gtkpod.  When importing the files and saving the changes everything seems to go fine, but when I disconnect and go to "Videos" I can see the videos but every single one is 0:00 seconds long and I just get a black screen when I play them.

I've tried multiple files, I've tried multiple format and they either won't Sync to the ipod at all or give me 0 seconds.

Any help would be great

Thanks in advance,
Tommah

Ubuntu 10.10 32bit
gtkpod
Ipod Video 2nd gen. 80gb Black

---

### Post by wolfen69 on 2011-11-03
What type of video files are you trying to put on it? ipods iirc, only support mp4 video.

---

### Post by tommah04 on 2011-11-03
> **wolfen69 said:**
> What type of video files are you trying to put on it? ipods iirc, only support mp4 video.

Well I tried almost all the presets available in FFMPEG (WinFF GUI).  I haven't seen an option for mp4, the closest is the mpg format that gives the 0 seconds on the ipod 

if there are more options that WinFF is showing that would be great to know

---

### Post by wolfen69 on 2011-11-03
Handbrake will convert to MP4.
```
sudo apt-add-repository ppa:stebbins/handbrake-snapshots

```
then
```
sudo apt-get install handbrake-gtk
```

---

### Post by wolfen69 on 2011-11-03
For some reason I am not able to add the repo via command line. However, I was able to add **ppa:stebbins/handbrake-snapshots** in synaptic. Handbrake installed just fine.

---

### Post by tommah04 on 2011-11-03
> **wolfen69 said:**
> For some reason I am not able to add the repo via command line. However, I was able to add **ppa:stebbins/handbrake-snapshots** in synaptic. Handbrake installed just fine.

that did it!  Thanks, I knew it was probably a format problem.

again, thank you so much

---

