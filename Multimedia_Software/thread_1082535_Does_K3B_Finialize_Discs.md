---
title: "Does K3B Finialize Discs??"
date: 2009-02-27
forum: Multimedia Software
---

### Post by umechanism on 2009-02-27
How do I make K3B finalize a video DVD that I am burning?  I've looked around but I can not determine how to finalize the session.  Any ideas?

Thanks!

---

### Post by wolfen69 on 2009-02-27
why is finalizing important? if you don't pop it in and try to burn again, then nothing will happen.

i don't have k3b installed at the moment, but i'm sure (100%) you can finalize. look around some more. it's usually an option right before you hit the "burn" button. just make sure it's not multisession.

---

### Post by umechanism on 2009-02-27
A non-finalized disc will not play in standard home DVD players (at least not in mine).  I've made several backup discs which contain the Audo_TS and Video_TS folders of my video DVD data.  I burn them to disc using K3B's "Video DVD" sessions.  The burn works just fine and my computer's DVD player will play the discs but my home DVD player will not.

The discs just need to be finalized so that the index is closed.  Then they will work on any DVD player.

---

### Post by umechanism on 2009-04-24
I still have not found a resolution here.  Bump.

---

### Post by milky2313 on 2009-05-29
I have the same problem.  You can close a multisession cd with K3B but only if you add at least one more file to burn.  I cannot find any burning program within ubuntu to finalize a disk without adding any more files.  My only (and quite undesirable) solution is to boot up windows and finalize the disk using Sonic.  

Too bad K3B doesn't have a simple "Finalize Disk" button, I will keep looking around though...

---

### Post by ..ken.. on 2009-12-20
In K3B, after you click on the "Burn" button you will get an options dialog. On the top right drop down change the "Writing App:" from "Auto" to "growisofs". That should do it.

---

### Post by cotcot on 2009-12-20
I remember that I had the same problem some time ago. It was a bug with the 'genisoimage' version that came with hardy. I see you have hardy. 
You can find [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5217002#post5217002") a MAYBE solution from that time. Please be careful with it. For me it was no solution. I think it is better to upgrade to 9.04 or 9.10 (or make a dual boot with a more recent ubuntu version). 
You could try a live CD to burn your stuff.

---

### Post by neuropa on 2010-06-21
I have the same problem!
I want to finalize a DVD created with an ecograph. Using Nero in Windows I can finalize the disk. How can I do the same with Ubuntu?

Thanks...

---

