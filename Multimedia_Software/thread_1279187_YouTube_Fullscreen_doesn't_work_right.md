---
title: "YouTube Fullscreen doesn't work right"
date: 2009-09-30
forum: Multimedia Software
---

### Post by sbelz79 on 2009-09-30
I can watch YouTube videos just fine- in regular and HQ, but when I maximize the window to fullscreen, it gets ridiculously choppy, and the controls gain a serious delay- it can take up to 10 or 15 seconds to exit fullscreen after hitting esc.  I don't have this problem when watching fullscreen videos on adultswim.com

I'm running Ubuntu 9.04 on an older machine.  I've got a 2.0 GHz AMD Athalon XP 2400+, 1GB of RAM, and an asus v7100 PRO AGP 32-bit card with 128MB of RAM and an nVidia GeForce MX 400 GPU.

---

### Post by psychok9 on 2009-09-30
I've the same problem only with native 64 bit version (and work very better with 32bit wrapper installed from synaptic).
Anyway try this:
LD_PRELOAD=/usr/lib/libGL.so.1 firefox

---

### Post by sbelz79 on 2009-09-30
> **psychok9 said:**
> I've the same problem only with native 64 bit version (and work very better with 32bit wrapper installed from synaptic).
Anyway try this:
LD_PRELOAD=/usr/lib/libGL.so.1 firefox

Tried it, restarted my computer, still having the same problem.

---

### Post by wojox on 2009-09-30
Look here under Flash Optimization: [http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005)

---

### Post by psychok9 on 2009-10-01
> **sbelz79 said:**
> Tried it, restarted my computer, still having the same problem.

How you have installed flash plugin?
You have modified firefox launcher/shortcut or you have tried where?

---

### Post by sbelz79 on 2009-10-01
Thanks for the suggestions, everyone, but the problem took care of itself when I upgraded my AGP from a 32-bit 128MB card to a 64-bit 512MB card.  Fullscreen works great in Youtube now, even in HQ.

---

### Post by psychok9 on 2009-10-01
Nice! I'm happy for you!
Can you specify the previous gpu and the actual gpu?
I suppose the previous it is Asus v7100 PRO AGP...(?)
Can be important for all users and my future experience :)

---

### Post by sbelz79 on 2009-10-01
> **psychok9 said:**
> Nice! I'm happy for you!
Can you specify the previous gpu and the actual gpu?
I suppose the previous it is Asus v7100 PRO AGP...(?)
Can be important for all users and my future experience :)

Previous AGP card:  ASUS v7100 Pro 32M with nVidia GeForce MMX 400 GPU.  128MB RAM

Current AGP card:   ZOTAC ZT-62AAH2N-HSL GeForce 6200 512MB 64-bit GDDR2 AGP 4X/8X

---

### Post by Tapas Pain on 2010-02-27
I know this thread is marked as solved but I figure other people might visit it and your solution might not work for them (as it didn't for me).  Here's what I found for me ... the problem was that I was running compiz fusion.  So, if you want to view YouTube videos in full screen without getting a bunch of headaches, open terminal and type
metacity --replace &
then you can view the YouTube videos in full screen.  When you're done and want to revert to compiz, type into terminal
compiz --replace &
Not so much for you, but for any newbies like me searching this thread.

---

### Post by Benj_C on 2010-07-06
I know the title says Solved, but I find that a bit crappy, since the solution was to change the graphic device....

Plus I've got the same problem, except I'm running Lucid, and none of the above solution worked for me. Anybody out there with a real solution?

---

