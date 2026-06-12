---
title: "Lockups and more"
date: 2009-04-20
forum: Mythbuntu
---

### Post by gmurison on 2009-04-20
I started to notice that my myth backend/frontend is loking up alot. I even noticed an error: mythconverg/program is marked as crashed. I tried to load the livecd, but the grub loads too fast.

While the system was up and running for a short time, I managed to run optimize_mythdb.pl and mysqldump to a file, which is on a backup USB drive.

So i am thinking that I will need to reinstall>>>I have another drive to install mythbuntu on, but will I be able to point it to the old recordings?  My initial thought is that it has something to do with the fstab/mount options??

Thanks, not quite e newb, but certainly no guru. I will try to get logs if that will help, but I am sure all is lost.

---

### Post by klc5555 on 2009-04-20
> **gmurison said:**
> I started to notice that my myth backend/frontend is loking up alot. I even noticed an error: mythconverg/program is marked as crashed. I tried to load the livecd, but the grub loads too fast.

While the system was up and running for a short time, I managed to run optimize_mythdb.pl and mysqldump to a file, which is on a backup USB drive.

So i am thinking that I will need to reinstall>>>I have another drive to install mythbuntu on, but will I be able to point it to the old recordings?  My initial thought is that it has something to do with the fstab/mount options??

Thanks, not quite e newb, but certainly no guru. I will try to get logs if that will help, but I am sure all is lost.

As long as you have your actual recordings, nothing is ever completely lost. You are in even better shape, because you also have a backed-up mythconverg

But first, are you sure this is software? Frequent lockups tend to be caused by deteriorating hardware, rather than software corruption (though enough crashes will eventually corrupt the software too.)

If you can correctly diagnose a hardware issue, you may not need to reinstall anything; if the problem is in fact hardware, six OS reinstalls will not help you.

Initial hardware suspects are anything that moves: CPU fans fail, or gum up with pet hair, and a system quickly overheats and locks up; ditto with case fans. Power supplies that come bundled with cases are very cheaply made and frequently go wonky. They can then begin to deliver dirty power that causes lockups which look like a variety of memory errors, right up to the time when they go >bang< in a shower of sparks (as happened to me a couple of weeks ago). And, finally, hard disks can go bad also.

So, can you keep your hardware running when no installed software is involved? Go into your bootup hardware setup and go to the screen that is labelled something like "PC-Health". Don't do anything there; just note the bootup CPU temperature and whether the bios thinks the CPU and/or case fans are running, and then, if they are, leave the machine running on this screen for a while to see whether a)the CPU temp seems to be going up precipitously (i.e. above 95 C for any AMD processor and, say, 60-70 C for an Intel), and/or b)the machine just dies running this screen.

If the machine is overheating here, then clean up and restore cooling fans as necessary. Sometimes a CPU will build up what amounts to a little felt blanket on top of the heat sink but below the fan blades of the CPU cooler, so that the cooler fan spins away but doesn't actually cool much until you (delicately) remove the buildup. 

If there is no heat buildup but the machine crashes on this bios screen anyway, then begin to suspect your power supply. If the machine won't crash on this screen at all, then you're ready to see if the machine can boot from a CD and run indefinitely so booted. Change your bootup sequence in the appropriate setup screen to put CD boot in the 1st position, then boot from a CD. Let the machine run at length and do whatever you can do with it from a CD boot.  If the machine crashes here, it again is likely either thermal or power supply problems. A quick reboot to bios can check the former. If temp is not a problem but the machine crashes when put under load (doing whatever you can do from the CD boot) then again, power is the likely culprit.

If the machine passes all of these tests, then it will be time to move on to other possibilities.

---

### Post by gmurison on 2009-04-28
Hi, just wanted to update this thread and marked it as solved, incase anyone else comes across a similar problem.  

End result was faulty hardware, I had a REALLY cheap video card in the system and upgraded it slightly, performance is much better.  The recordings seem better too.

I also discovered that I was plagued the dreaded Seage 7200.11 firmware issue and had the drive replaced.

As klc5555 (props) suggested, perform exhaustive diags before jumping to the software conclusion.

---

