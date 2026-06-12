---
title: "installing GMA500 drivers on WEBS 1010"
date: 2010-04-03
forum: Multimedia Software
---

### Post by boazin on 2010-04-03
Hi all,
 
I have a portwell WEBS1010 mini PC ([http://www.portwell.com/products/detail.asp?CUSTCHAR1=WEBS-1010](http://www.portwell.com/products/detail.asp?CUSTCHAR1=WEBS-1010)) which I tried to install ubuntu 9.10 on.
 
It contains the cursed GMA500 chipset and supposed to be similar to all the other devices containing it
 
I tried everything there is, all the posts and methods
([http://swiss.ubuntuforums.org/showpost.php?p=8182373&postcount=87](http://swiss.ubuntuforums.org/showpost.php?p=8182373&postcount=87)
[http://ubuntuforums.org/showthread.php?t=1229345&highlight=GMA500](http://ubuntuforums.org/showthread.php?t=1229345&highlight=GMA500)
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/))
 
all getting the same results, some of them are installing fine but when I reboot, I get an error message from X telling me there was an error and I can only move to low-graphics mode.
 
I've attached to error log. Can someone please try to help me here?
 
Thnaks,
Boazin

---

### Post by mikewhatever on 2010-04-07
Judging by the picture, the device in question is remarkably similar to the one found at [http://www.fit-pc.com/web/](http://www.fit-pc.com/web/). Now, those guys have a forum with instructions detailing what to do.

[HOWTO]("http://www.fit-pc2.com/forum/viewtopic.php?f=43&t=1150&sid=1dcbe6581d6eb6e30b79452ad8c58ea9")

[Live cd]("http://www.fit-pc2.com/forum/viewtopic.php?f=43&t=1543&sid=1dcbe6581d6eb6e30b79452ad8c58ea9")

---

### Post by boazin on 2010-04-10
YES!!!!!! It worked.... thank you very much!
 
No lag now on normal work
 
Some problems with 720p videos, there is a hickup and than a loss of sync between the video and the audio. (on mPlayer)
 
I think I'll try VLC,
 
any thoughts?

---

### Post by boazin on 2010-04-10
Well, the joy was a bit too soon.
 
Apperantly X alone (on full idle) takes about 40% of the CPU.
 
For some reason mplayer manages not to pass 100% so its fine, but the moment the 100% reaches the bideo and the audio lose sync. 
 
VLC turns out crappy here. not a single frame is shown properly.
 
What else can I do?
 
(xorg.conf will be uploded in a few hours)

---

### Post by mikewhatever on 2010-04-10
VLC can be configured to use other then default video outputs under Edit->Preferences->Video. Try selecting vaapi if available. That said, I doubt it will do any better then mplayer.
Xorg idling at 40% cpu is rather high, and hopefully there is a solution. I don't have that kind of device, just a netbook with the same chipset, a dell mini 10, but xorg gives no such issues. i720 videos are hit and miss, some play ok, while others stop and stutter.

---

### Post by boazin on 2010-04-10
thanx,

maybe still someone has a clue if there is something to be fixed in the xorg.conf,
all the posts I see are not similar to the configuration the above howto did (IEGD)

---

### Post by mikewhatever on 2010-04-10
```
Modes     "1920x1080"
```

Is that really the resolution you use (the only mode available in xorg.conf)?

---

### Post by boazin on 2010-04-17
(back in business)
No. I switched to 1360X768 in the "display" app on X.

tried to change the line you said to 1360X768, no change.

Do I need to put something special there? what is the depth I need to put?

---

