---
title: "Locking up while watching a recording in progress"
date: 2010-08-21
forum: Mythbuntu
---

### Post by agentsmith23 on 2010-08-21
I watched my first NFL game using myhtTV last night and I was very disappointed. The game completely froze about 6 time while watching the game and the frontend became unresponsive. I had to use the system monitor to force the frontend closed. Every time it would lock up it would show that it was around 98% CPU load. When I started it back up and tried  to go to the exact same spot where it froze earlier it would lock up immediately. If I would skip past that part it was fine for a little while but it would eventually do it again. 

I also get this one annoying problem that I have always had on mythtv and have yet to figure out how to fix it. It seems like there is some kind of tearing going on. I'm not quite sure what to call it but there is a horizontal separation in the picture that slowly scrolls down the entire screen and it happens like maybe once every 2 min or so. It doesn't really effect viewing too much but you can definitely tell that it shouldn't be there. it also looks similar to distortion that I notice when using Compiz and using the cube and some other effects.

I'm not sure if these problems are caused by my hardware or if it is software. Here are the specs of my HTPC:

AMD Athlon 7850 Dual Core
Gigabyte MA78GM-US2H motherboard
Built in Radeon 3200 video card
4GB ram
Hauppauge 1600 tuner
Resolution is set at 1280x720

If any more info is needed please ask.

---

### Post by winewood on 2010-08-21
Its my opinion that the graphics card is the weakest part of your entire setup.  A new and FAR more powerful graphics card can be obtained for $100.  If you have no cash, simply borrow an old card from a power user who has upgraded recently.  Integrated graphics cards when pressed have a tendency to overheat easiliy.  Many case setups do not have a fan even designed to cool them off.  
 
Its safe to say that for any HD graphic application or game worth playing, that integrated graphics should only be used for the most basic of work applications or conifguring the box, not for displaying graphics of any quality.

---

### Post by tgm4883 on 2010-08-21
You were experiencing vertical tearing, which IIRC is fixed by vsync. You probably need to upgrade your video card

---

### Post by LowSky on 2010-08-21
No need to spend $100, [This one ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814162040") is availble for $40 after mail in rebate.

---

### Post by agentsmith23 on 2010-09-10
I got a new video card yesterday, it is a GT240 [http://www.frys.com/product/6219310?site=sr:SEARCH:MAIN_RSLT_PG]("http://www.frys.com/product/6219310?site=sr:SEARCH:MAIN_RSLT_PG")

Just working on getting the audio working and I will see if the tearing is resolved.

---

### Post by larsolav on 2010-09-10
Just in case it slips your mind, once you get it working, remember to set up the playback profile in the frontend to some version of VDPAU...

---

