---
title: "Cannot play indeo 5 files (vid_iv50.xa files)"
date: 2009-11-22
forum: Multimedia Software
---

### Post by kenji_03 on 2009-11-22
So yeah, Ubuntu noobie here.  I have a file that mplayer tells me is indeo5 format and it won't play (here is a sample video of [inedo 5]("http://samples.mplayerhq.hu/V-codecs/IV50/indeo50.avi") format before you go out praising your VLC or what have you players)

I don't know if I am on x32 or x64, so the first question is how do I figure that out?  It seems from [my research]("http://ubuntuforums.org/showthread.php?t=915257") that anyone with an x32 system won't have problems while x64 users will.  (For clarifications sake, this thread is a 9.10 help thread, the research thread is like 6.xx)

The second question is two fold, on the first hand if I am running a x32 system and I cannot run the file, how can I?  Secondly, if I am on an x64 system and cannot run the file, how can I as well?

Thank you all in advance as I know this awesome forum community will come through for the greater good of us all ^.^!

---

### Post by mc4man on 2009-11-22
On a 32 bit install mplayer or a xine based player will playback if w32codes are installed (as far as xine, I tested with xine and a redone totem-xine

to ck arch
```
uname -m
```

w32codecs can be installed after adding medibuntu repo 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

or directly by dl'ing and d. clicking on .deb (find in home folder
```
wget http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu5_i386.deb
```

for 64 bit install you can build and install a 32 bit mplayer (involved
or
install wine and run a windows mplayer (fairly easy

---

### Post by kenji_03 on 2009-11-23
I will try that as soon as I get home, thank you so much!

---

