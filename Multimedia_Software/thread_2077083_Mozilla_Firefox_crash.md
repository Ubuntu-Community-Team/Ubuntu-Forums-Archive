---
title: "Mozilla Firefox crash"
date: 2012-10-27
forum: Multimedia Software
---

### Post by acefromspace on 2012-10-27
I'm using a fresh install of Ubuntu 10.04 (everything updated)
When using Firefox, and trying to download videos (from that very popular website) I limit it to two downloads at a time (slow computer: CPU 1800 MHz, Ram 512 MB) My internet is reasonably fast (3 MB) Using VideoDownloadHelper (worked fine before with 10.04) Downloads progressing until I click on another video (or hit back button), then Firefox crashes. Disabled hardware acceleration (in firefox)... still crashes. When I close and restart Firefox, no homepage. When I try to download again, it resumes the previous downloads where they left off. I'm not able to watch flash video (but don't care... just download mp4 and watch later... I hate flash) Everything worked fine before (10.04 and VideoDownloadHelper... same website) so could it have to with the updates? I did the fresh install because I switched hardrives (didn't do updates on old system, that's why I suspect that could be related to problem) I have older NVidia card and using propietary driver (recommended) same as before. Should I change settings in video card? Seem to remember disabling hardware acceleration that way before. Same computer... no changes, so I don't think it's a memory issue. Maybe need older version of Firefox? I have Chrome but haven't tried it yet. Will post if any issues show up with it. Anyone else having similar issues?

---

### Post by Abhinav Kumar on 2012-10-27
Hey acefromspace,
could you please try flashgot with mozilla firefox.

---

### Post by kurt18947 on 2012-10-27
I've had some functional problems a couple days ago with VideoDownloadHelper.  I tried a different download extension (can't tell you which one) which worked better.  I was using 12.xx and Firefox 16.01.

---

### Post by acefromspace on 2012-10-29
Abhinav Kumar, I have Flashgot, but don't know how to use it. Any tips?

---

### Post by acefromspace on 2012-10-31
I remembered one thing I did different this time that might have caused trouble... IcedTea java plugin. Actually, I just did another fresh install and will not use iced tea this time (checking into oracle java instead)

---

### Post by acefromspace on 2012-10-31
Everything seems to be working... no firefox crash. I removed my graphics card this time (NVidia) and used onboard graphics (VIA) My best guess is that the NVidia card was the issue. I don't do gaming and no need for 3D, so onboard graphics is fine. NOTE: small fan on graphics card was shot so I had removed it, but it worked fine like this before... maybe it was overheating, but strange it worked all summer... it's an old card, maybe just it's time to go?

---

### Post by acefromspace on 2012-10-31
Mozilla firefox just crashed again... not a hardware issue (had nothing to do with video card) I updated my install and firefox changed from 10.xx to 16.xx (sometimes I wonder if it's worth updating at all?) I also did post-install of multimedia stuff (ubuntu freak's sticky) but used the same method before with no issues (firefox crash) I'm going to upgrade to ubuntu 12.04 soon, but I don't like mysteries... still need to know why this happens. I disabled iced tea, but didn't help (it loaded when I did the multimedia stuff, but wasn't on the list... must have been included somehow) This is either java related or firefox... I was not doing any downloads when it crashed. Is this related to flash? How is it that something as crappy as flash could cause so many issues? On a side note: I tried flash-aid with no luck, but videodownloadhelper works!

---

### Post by acefromspace on 2012-11-06
I removed all java stuff... no more crash. Going to try to manually install newer version of java.

---

### Post by acefromspace on 2012-11-13
Seems to be a java issue. I've installed java again (newest oracle version) and same problem (firefox crash) but only have problems when downloading videos. I just turn off java when doing video downloads, and turn it back on for everything else (temporary workaround, but not real solution)

---

