---
title: "Coverting Quicktime Files"
date: 2012-08-12
forum: Multimedia Software
---

### Post by Aliofthecia on 2012-08-12
Hey 

I'm new to Ubuntu and I'm having problems trying to convert .mov files. Originally they
were files from FCP on my Mac that I exported onto my portable hard drive as quicktimes. I've tried using ogg and transmageddon with no luck. Tried downloading all
the Gstreamer codecs etc. Does anyone have any suggestions? 

Much Appreciated.

---

### Post by ads52 on 2012-08-13
If you were prepared to use the commandline FFmpeg would be a good option to try. But do these files not simply play under Ubuntu?

---

### Post by Aliofthecia on 2012-08-13
They simply do not play. I get a message saying error cannot decode stream.

---

### Post by lukeiamyourfather on 2012-08-13
> **Aliofthecia said:**
> They simply do not play. I get a message saying error cannot decode stream.

What codec did you use originally?

---

### Post by ads52 on 2012-08-13
> **Aliofthecia said:**
> They simply do not play. I get a message saying error cannot decode stream.

Is it possible that you can post one of these files somewhere? I have a suspicion that with a bit of fiddling they should play as they are on Ubuntu.

---

### Post by Aliofthecia on 2012-08-13
It says the Codec is a DV video

---

### Post by ads52 on 2012-08-14
> **Aliofthecia said:**
> It says the Codec is a DV video

I believe that *ffdv* is suited for this so a decent copy of MPlayer should be able to play the files. Perhaps try the following in a terminal:

```
sudo apt-get install mplayer libavcodec-extra-53 smplayer
```

Then try the file with SMPlayer...

---

### Post by Aliofthecia on 2012-08-14
I tried to open with SMplayer but it wont even recognize the files. I probably should of put this in
my original post but i'm trying to move the files from my Mac because the dvd burner is shot to my laptop which is a PC. The two computers obviously don't like each other cause they are not cooperating...

---

### Post by ads52 on 2012-08-14
Is there any chance you could post one of the troublesome files online? I believe RapidShare is still operating if you do not have your own access.

---

### Post by Aliofthecia on 2012-08-14
Hey I've made a rapidshare account and am currently uploading one of the files but it is slow going i'll let you know when its uploaded

---

### Post by bcarlowise on 2012-08-14
Try using Openshot Video Editor to save the file as another format. My camera saves movies as .mov files and I use Openshot to convert them to MPEG or MP4.

---

### Post by ads52 on 2012-08-15
> **Aliofthecia said:**
> Hey I've made a rapidshare account and am currently uploading one of the files but it is slow going i'll let you know when its uploaded

Looking forward to testing out your file :)

---

