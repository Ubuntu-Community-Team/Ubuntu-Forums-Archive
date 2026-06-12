---
title: "Front hangs due to backend usage in combined system.  Need to keep some memory free?"
date: 2009-07-15
forum: Mythbuntu
---

### Post by yeppp on 2009-07-15
[SIZE=4]I recently built a combined frontend-backend mythbuntu system an AMD dual core processor, 4 gigs of ram, and an intergrated graphics card.  I have found that apparently the backend takes up all my ram in cache.  My problem occurs when I start using the frontend, while the backend is recording shows.  The frontend will become very slow to respond. 

The only reason I could think of is the backend's cache is not elimated quick enough for intergrated graphics card to use.  If this is the case I need to limit the amount of ram the backend can use to leave some always free for the frontend, and I'm not sure how to do that.  I'm obviously not sure about any of this; so, what could be the problem and how would I solve it?
[/SIZE]

---

### Post by ian dobson on 2009-07-16
Hi,

4Gb ram is more than enough for a combined backend/frontend. Why do you thing the backend is using too much memory? The mythbackend process only needs about 40-80Mb ram from my experience. On linux any unused memory is used by the disk cache which can be freed very quickly if required.

Could you try start a terminal session then run the program top to see whats using your CPU. If the system is becomming unresponsive then it's usually the CPU thats getting hit.

You say your using an onboard graphic card, but you don't say which one. Have you loaded the correct drivers for it?

When recording mythbackend starts a commflag process that attempts to mark commercial breaks, the can put the CPU/harddisk under pressure. Running top will let you see whats hitting the CPU.

Regards
Ian Dobson

---

### Post by yeppp on 2009-07-16
[SIZE=4]Thank you for the reply!  I figured that the 4 gigs and the amd Athlon 64bit X2 2.3 GHz would be more than enough muscle for everything thrown its way, so all I could figure was the onboard video card wasn't able to ascess the memory quick enough (a long shot, I know).  It is a NVidia GForce 8200.  

Your probably right about it being something hitting the processor.  I'll run the top command this afternoon when it normally bogs down and see what it gives me and post it.  If it is commerical flagging how do I get that to slow down and not eat all of the processor?  Thanks!
[/SIZE]

---

### Post by ian dobson on 2009-07-16
Hi,

What graphics driver are you using? I would recommend using the NVIDIA proprietary, it's much better than the open source one.

Regards
Ian Dobson

---

### Post by yeppp on 2009-07-16
I am currently using the NVIDIA driver which is working well.  Right now my mythbox is commerical flagging 1 show and the process is taking up to 20% of the cpu.  At times it could be flagging two shows at once, so it is very possible that this is the culprit.  I'll look around for this too, but is there a way to do all the commerical flagging late at night or make it take run slower (using less cpu)?  Thanks for the help.

---

