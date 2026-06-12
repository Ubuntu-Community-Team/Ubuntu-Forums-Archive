---
title: "VLC doesn't play any more videos"
date: 2010-08-14
forum: Multimedia Software
---

### Post by freeball1 on 2010-08-14
Hi all, I added the [Cutting Edge Multimedia PPA ]("https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia") to my repositories and upgraded all packages.
Now VLC won't show videos anymore, error messages like this (also for other codecs):
```
No suitable decoder module:
VLC does not support the audio or video format "mp4v". Unfortunately there is no way for you to fix this.
```
I can hear the video's sound though.

Any help?

---

### Post by freeball1 on 2010-08-14
I just noticed, that mplayer/smplayer won't play the files either:
```
error while loading shared libraries: libva-x11-0.31.1.1.so.1: cannot open shared object file: No such file or directory
```

But Playback with Banshee works perfectly :confused:

Am I missing any codecs (maybe removed by the upgrade)?

---

### Post by freeball1 on 2010-08-17
bump

---

### Post by cchhrriiss121212 on 2010-08-17
I always just go for the restricted-extras package, do you have the newest version of that?
You could always look through your history and see if the upgrades took out anything.

---

### Post by freeball1 on 2010-08-17
I have that package, but I noticed all works again after purging the ppa, so it must have something to do with the upgraded packages...

---

### Post by eightdollarbeer on 2010-08-18
yes same problem here for such a good ppa i don't want to loose it due to this.i thought i was going mad when totem played something vlc wouldn't.
please fix ppa.

---

### Post by freeball1 on 2010-08-21
@eightdollarbeer or anyone who might have had this problem, please post in this thread if you notice it works again, because i don't want to add the repository every 2 days just to see it still doesn't work and purge it again...

---

### Post by eightdollarbeer on 2010-08-22
I have just retried with only your ppa activated and it fails the same. i can not make sense i have a server running your ppa and it works. i originally thought multiverse messed it up .
let me know when its update i will try again.
thanks

---

