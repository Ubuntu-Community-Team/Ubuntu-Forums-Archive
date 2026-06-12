---
title: "Is 3d gaming &amp; compiz-fusion possible with ati radeon card?"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by Original Brownster on 2007-10-17
Hi, I'm running Gutsy Gibbon and have an ati radeon 9600 pro card which works with gaming fine with the fglrx driver under fiesty and Gutsy, but when I enable the composite extension in my xorg.conf file and install xserver-xgl I get the 3d desktop working ok nice and fast but my games no longer work (doom3), going back to old settings and it works.
Does anybody know if this is a configuration issue by me or a driver issue?

---

### Post by bromix on 2007-10-17
I have the same card and am using Gutsy as well.  I play WoW and NWN.  Neither one work very well at all with compiz-fusion under xgl.  Quite frankly, it doesn't bother me because when I want to play, I play the game and don't use the desktop, not to mention it frees up resources on my humble system.  The hanger being that with Gutsy, xgl starts by itself and  there isn't a session choice at login. 

 What I did for a workaround was to create another user.  


Then, in that users home directory, enable view hidden files.  

Then in the ./config folder  create a folder named "xserver-xgl"      

Inside that folder create an empty text document titeld "disabled".   

 When you log into that users account xgl will not start and your games should play fine.   Let me know if I confused you, or if you need speculation

---

### Post by bromix on 2007-10-17
This was found on launchpad in case you have any doubts

* Add a killswitch to disable Xgl on a per-user basis. If the file
    ~/.config/xserver-xgl/disable exists, Xgl will not be automatically
    started. Documented in README.Debian. (LP: #136878)

[https://launchpad.net/ubuntu/+source/xserver-xgl](https://launchpad.net/ubuntu/+source/xserver-xgl)

---

### Post by blazercist on 2007-10-17
This is a limitation of fglrx driver.  The problem being that it cannot handle AIGLX or composite.  AIGLX support is to be included in fglrx 8.42 due sometime this month.  If 8.42 provides working AIGLX support your issues should go away.  So in short, pray for a fast/working/AIGLX supporting fglrx 8.42 sometime in the near future.

Or, a temporary fix, you could run games in Xnest or a new X session.  Theres a winewiki entry that deals with this, you can find it by searching winehq.org

---

### Post by bromix on 2007-10-17
Yeah, you could wait, or just use the simple solution of another user account with the killswitch like I posted.

---

### Post by Original Brownster on 2007-10-17
> **bromix said:**
> I have the same card and am using Gutsy as well.  I play WoW and NWN.  Neither one work very well at all with compiz-fusion under xgl.  Quite frankly, it doesn't bother me because when I want to play, I play the game and don't use the desktop, not to mention it frees up resources on my humble system.  The hanger being that with Gutsy, xgl starts by itself and  there isn't a session choice at login. 

 What I did for a workaround was to create another user.  


Then, in that users home directory, enable view hidden files.  

Then in the ./config folder  create a folder named "xserver-xgl"      

Inside that folder create an empty text document titeld "disabled".   

 When you log into that users account xgl will not start and your games should play fine.   Let me know if I confused you, or if you need speculation

Thanks for the tip, that's a useful workaround which it seems I will need for a while yet!

---

### Post by Original Brownster on 2007-10-17
> **blazercist said:**
> This is a limitation of fglrx driver.  The problem being that it cannot handle AIGLX or composite.  AIGLX support is to be included in fglrx 8.42 due sometime this month.  If 8.42 provides working AIGLX support your issues should go away.  So in short, pray for a fast/working/AIGLX supporting fglrx 8.42 sometime in the near future.

Or, a temporary fix, you could run games in Xnest or a new X session.  Theres a winewiki entry that deals with this, you can find it by searching winehq.org

Thanks, I was wondering if it was me being dumb. I have to confess I'm finding it hard to understand how all these different elements of the windowing system work together, the x server was hard enough I thought. 
If the new driver works will it simply be a matter of enabling AIGLX in my xorg.conf file (currently it's disabled) and is this used as well as xserver-xgl which I installed? 

I'll look at Xnest too thanks, at least I should be able to get a game now!

---

### Post by bromix on 2007-10-17
AIGLX is inside of xorg, rather than running on top of it like XGL does.  I'm by no means on expert on the issue, so I don't know the specifics of a performance comparison.   But, I'm guessing performance would be better.  When the time comes, you would not need xgl anymore.  Would be one or the other.   I'm gonna do some googling on "AIGLX vs. XGL"  just for my personal knowledge.

---

### Post by blazercist on 2007-10-17
Yes is order to get desktop effects wiith the current fglrx driver you need to disable AIGLX and Composite in xorg.conf.  When ATI releases the (hopefully working and AIGLX compatible) 8.42 driver, then all you will have to do is remove xserver-xgl package and the xgl startup script or just go back to the default gnome session instead of your xgl one, then you would take out the entries referring to AIGLX that you added to your xorg.conf.

The performance gains with AIGLX versus XGL are huge, not to mention that the performance gains of 50-90% with the fglrx 8.41.7 driver will be backported to support the r300/400/500/600 cards in 8.42 if I'm not mistaken.

Like I said, 8.42 will solve numerous problems with compatibility and performance if it is all that ATI makes it out to be.  So you just have to sit and wait for them to release it.

Just so you get an idea of XGL versus AIGLX, AIGLX is standard since feisty whereas XGL is commonly called a "hack" by devs.  XGL eats up as much as 50% of my 2.2GHz Turion64 at times whereas I've heard that AIGLX never uses over 10% of the CPU.  AIGLX is so efficient that you can play 3d games with unnoticable side effects/performance drops.  So AIGLX is the way to go if possible.  This is why NVidia GPU's are so Linux freindly-- that is because of they vastly superior drivers.

If I had known about this prior to buying my laptop and discovering linux I would have gone Intel/NVidia instead of AMD/ATI.

---

### Post by Original Brownster on 2007-10-17
I was wondering how nvidia stacked up against ATI these days, I haven't looked at cards since buying my radeon 9600 probably about 3-4 years ago. I remember at the time checking for linux compatibility and thought it would be ok only to find that the drivers were incomplete, some of the games I played would not work fully due to this. Previously I had nvidia cards and had no problems at all. 

From what you are saying nvidia are still the best for linux driver support.
I am thinking about building a new pc in the near future so I expect this time it will be nvidia unless things change substantially by then.

Thanks again for all the info.

---

### Post by blazercist on 2007-10-17
Nvidia have better driver support for linux AND windows in my opinion, its a fact in linux.  And yes if you are building a new PC and want good driver support I suggest NVidia.   Even if ATI comes out with a good working driver in 8.42 they are still like a year or two behind Nvidia.

---

