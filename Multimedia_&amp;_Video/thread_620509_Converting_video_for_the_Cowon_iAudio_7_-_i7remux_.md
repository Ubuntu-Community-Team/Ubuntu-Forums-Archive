---
title: "Converting video for the Cowon iAudio 7 - i7remux tool"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by little_penguin on 2007-11-22
To convert video that will play on the iAudio 7 without having to use the JetAudio software, which is Windows only, follow the instructions here:

[http://iaudiophile.net/forums/showthread.php?t=16285&highlight=i7remux]("http://iaudiophile.net/forums/showthread.php?t=16285&highlight=i7remux")

The guy on the iaudiophile forum has written a useful tool called i7remux which has to be run on the output of mencoder (or ffmpeg/transcode, whichever is used to rescale/convert the original video to iaudio 7 parameters).  It works, I've tried it. 

Before I discovered it, I'd tried for ages just using mencoder with all the right options and the exact parameters specified on Cowon's website, but the resulting converted videos would, for some reason, never play on the iAudio 7. The i7remux step is therefore crucial in getting them to work.

Just thought I'd pass that on.

---

### Post by daengbo on 2007-11-22
Thanks for that. Is there a wiki page we can put this and other portable player info on? I know people are having trouble with the iRiver Clix and Nokia videos, too.

---

### Post by little_penguin on 2007-11-23
Good idea - anyone started/know of existing Wiki for mp3 players? If so, they are welcome to include the above info.

---

### Post by wet_colored_arch on 2008-04-14
little penguin.. I am using Fiesty and cannot get i7remux to pass ./config

I am a noob, and first time installing tarball .. how did you get this to work?

---

### Post by little_penguin on 2008-04-26
> **wet_colored_arch said:**
> little penguin.. I am using Fiesty and cannot get i7remux to pass ./config

I am a noob, and first time installing tarball .. how did you get this to work?

Hi, I installed it by entering these commands, one after the other in this order:

$./configure
$ make
$ sudo make install

If this still doesn't work, could you post what error message(s) you are getting?

---

### Post by wet_colored_arch on 2008-05-02
I am not getting ./configure to work as below.. first time compiling as such but I thought this should be straightforward.  Any idea what is going on?  (currently on Heron)

checking for GNU make... make
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

do I have to go through synaptic and install each of these or???

---

### Post by little_penguin on 2008-05-03
It looks like you don't have the GNU C/C++ compiler installed yet. In a terminal:

```
sudo apt-get install build-essential
```

should install them, according to [https://help.ubuntu.com/community/InstallingCompilers]("https://help.ubuntu.com/community/InstallingCompilers")

Then try repeating ./configure

Hope it helps

---

