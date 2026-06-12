---
title: "Videos Close Immediately When Opened"
date: 2009-05-20
forum: Multimedia Software
---

### Post by gmtyrant on 2009-05-20
I've installed the restricted extras pack, so I ought to be able to play MP4 and AVI videos, but whenever I open one, the video player loads, and then closes immediately. I've installed VLC, but it does the same thing.

I'm a nooblet. Help?

---

### Post by jbruced on 2009-05-20
I had the same problem with compiz effects on at one time. It seemed to be a resources thing.

My 2 cents

---

### Post by andrew.46 on 2009-05-22
Hi gmtyrant,

> **gmtyrant said:**
> I've installed the restricted extras pack, so I ought to be able to play MP4 and AVI videos, but whenever I open one, the video player loads, and then closes immediately. I've installed VLC, but it does the same thing.

Have you tried altering the video settings in:

Tools --> Preferences --> Video --> Output

to something like xv? I attach a screenshot to illustrate this, note that your version of vlc may look a little different but the option should still be there :-).

All the best,

Andrew

---

### Post by gmtyrant on 2009-05-23
I guess it could be resources... I'm only running on half a gig of ram.

I tried changing that setting, Andrew, to Xvideo. Same result.

---

### Post by andrew.46 on 2009-05-23
Hi again gmtyrant,

If you are keen to pursue this perhaps you could install a copy of MPlayer and run the file from the commandline as follows:

```
mplayer -v myfile.mp4
```

And then post the command + full terminal output here. The easiest copy of MPlayer is from [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") and grab the w32codecs while you are there. Running from the commandline might be the best idea anyway with a low resource computer.

All the best,

Andrew

---

### Post by gmtyrant on 2009-06-08
Sorry I hadn't replied sooner. Work got crazy.

Thanks so much for the suggestion... here is the output:

> Type: 0, display: 0x8d2c950, resourceid: 2e00006, serial: 7e9
Error code: b, request code: 84, minor code: 13
X11 error: BadAlloc (insufficient resources for operation)1.0% 66 0 

Over and over and over. Audio plays, but video is black. 512mbs of RAM ought to be plenty for playing a simple video file...

After closing Mplayer, I recieve this output:

> Uninit audio filters... 1.691 ct:  0.022 1057/1057 40%  7%  1.0% 224 0 
[libaf] Removing filter dummy 
Uninit audio: faad
FAAD: Closing decoder!
Uninit video: ffmpeg
Successfully enabled DPMS
GNOME screensaver enabled
vo: uninit ...

Exiting... (Quit)

---

### Post by andrew.46 on 2009-06-09
Hi gmtyrant,

> **gmtyrant said:**
> 
```
Type: 0, display: 0x8d2c950, resourceid: 2e00006, serial: 7e9
Error code: b, request code: 84, minor code: 13
X11 error: BadAlloc (insufficient resources for operation)1.0% 66 0 
```


My apologies but I am a little unsure as to how this error can be fixed. If nobody else can suggest a more *focused* fix for your problem perhaps you might consider trying this popular guide:

Comprehensive Multimedia & Video Howto
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

All the best,

Andrew

---

### Post by Scubdup on 2009-06-09
Install the Medibuntu stuff [here]("https://help.ubuntu.com/community/Medibuntu"). Seems to have worked for me.

---

