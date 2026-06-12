---
title: "fruity loops 7 in wine ...."
date: 2009-07-20
forum: Multimedia Software
---

### Post by dd1linux on 2009-07-20
I have everything working fine, except for the fact that the majority of the sound samples and packs wont play.  They are installed in the correct directory, but fl just wont read them.  I have run into this problem before and managed to correct it (with alot of assistance from forums like these), but i can't remember what i did.  I'm pretty sure its either some kind of registry thing or i need a .dll installed on my virtual C:/ drive.  Also, it may simply be that i need to download a new linux codec, because the sounds wont even play when i try to open them by browsing through the virual c drive. can anyone help me out?  Please just ask if you need more specifics

---

### Post by zetanuxi on 2009-07-21
I have the same problem with FLStudio 8 under wine.

But this just dawned on me. You were refering to codec packs. All of the samples are in .wav format, which is proprietary to Windows. Could you find a .wav codec for Ubuntu? That might fix the problem. :D

Here's a link within the forums to a .wav codec: [http://ubuntuforums.org/showthread.php?t=359375](http://ubuntuforums.org/showthread.php?t=359375)

---

### Post by dd1linux on 2009-07-22
Problem solved!  I found the tutorial i used the previous time.  Anyone experiencing similar issues refer to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7036](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7036) that fixed it for me (although you have to slightly edit the code in step 11 to accurately reflect the location of your system.ini file).  I haven't tested FL fully yet, but it got most sounds working.  I will try and make some music in the morning and hopefully let yall know if EVERYTHING works.

---

### Post by zetanuxi on 2009-07-22
What distribution are you running? I did some browsing on the Image-Line forums. FL 8 won't work at all for this issue. Anything pre-FL 8 only works in Hardy. :( Now, the 8.5 beta works perfectly in Jaunty, supposedly. I'll have to do some more searching, but I think that's about it.

---

### Post by dd1linux on 2009-07-22
im running jaunty 9.04 64-bit and FL 7 XXL

---

### Post by ubuntu27 on 2009-07-22
I don't know the solution to your problem as I never used Wine.
But, have you tried to use a native application?

There is a software called [LMMS]("http://lmms.sourceforge.net/") or [Linux MultiMedia System]("http://lmms.sourceforge.net/"):

[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)

Links to reviews:
 
[LMMS Turns Your Desktop Into A Music Sequencing Monster]("http://www.lifehacker.com.au/2009/04/lmms-turns-your-desktop-into-a-music-sequencing-monster/")


[LMMS Free Music Production Software: Free Open Source Alternative to FruityLoops]("http://www.ilovefreesoftware.com/20/windows/mp3/lmms-free-music-production-software-free-alternative-to-fruityloops.html")

---

### Post by dd1linux on 2009-07-22
> **ubuntu27 said:**
> I don't know the solution to your problem as I never used Wine.
But, have you tried to use a native application?

There is a software called [LMMS]("http://lmms.sourceforge.net/") or [Linux MultiMedia System]("http://lmms.sourceforge.net/"):

[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)

Links to reviews:
 
[LMMS Turns Your Desktop Into A Music Sequencing Monster]("http://www.lifehacker.com.au/2009/04/lmms-turns-your-desktop-into-a-music-sequencing-monster/")


[LMMS Free Music Production Software: Free Open Source Alternative to FruityLoops]("http://www.ilovefreesoftware.com/20/windows/mp3/lmms-free-music-production-software-free-alternative-to-fruityloops.html")


Yeah ... i tried that for a lil while, it's kind of like fruity loops little brother or something, but i got FL7 running quite well, good lookin out tho!

---

### Post by HunterThomson on 2009-12-01
> **ubuntu27 said:**
> I don't know the solution to your problem as I never used Wine.
But, have you tried to use a native application?

There is a software called [LMMS]("http://lmms.sourceforge.net/") or [Linux MultiMedia System]("http://lmms.sourceforge.net/"):

[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)

Links to reviews:
 
[LMMS Turns Your Desktop Into A Music Sequencing Monster]("http://www.lifehacker.com.au/2009/04/lmms-turns-your-desktop-into-a-music-sequencing-monster/")


[LMMS Free Music Production Software: Free Open Source Alternative to FruityLoops]("http://www.ilovefreesoftware.com/20/windows/mp3/lmms-free-music-production-software-free-alternative-to-fruityloops.html")


Hoe. . Nice, I remeber seing that in "Linux Journal" about a year ago. I just installed it now and boy it is alsom :) 

I am not a realy good DJ guy. I just want to play around now and agin. LMMS works quit well for me and I don't have to install 100MB of lib32's for Wine anymore. LMMS basicly is only lacking FLstudio fetures I don't know how to use any way. For me LMMS is a good fit and looks cool too.

kdenlive is good for video. Go OpenSource :)

---

