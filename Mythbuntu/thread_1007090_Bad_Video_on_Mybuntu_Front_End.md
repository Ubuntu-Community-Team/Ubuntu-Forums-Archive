---
title: "Bad Video on Mybuntu Front End"
date: 2008-12-10
forum: Mythbuntu
---

### Post by acmeinc on 2008-12-10
Xubuntu will not properly display the front end app of Mythbuntu.  The video is distorted in a downwards diagonal.  I am using a 512 PCI express ATI Radeon PCI-x card.  Any info or related problems?

---

### Post by onehotcutey on 2008-12-11
Just the problem I have been searching the forums to get solved.

I just built a new HTPC system:

AMD Athlon 64 X2 3800+
DViCO FusionHDTV7 Dual Express
OnBoard ATI Radeon HD 3200

So the system doesn't work perfect yet, the problem related to this thread is that when I start the MythBuntu frontend the graphic display get messed up, almost like a resolution change that doesn't quite complete.

It only happens in the Myth frontend, while the ATI proprietary driver is installed (version released on december 10, 2008).  When I disable this driver and reboot the Myth frontend begins working again though it's still choppy.  Reading through the ATI site, I'm sure it has something to do with the ATI driver (very sucky) but if anyone else has input I would love to hear it.

And just in case some wants to give some good advice here are my other two main problems:

2. The FusionHDTV7 Dual Express actually works and pulls in the QAM-256 channels (WOOOOHOOOOO) but it has 2 tuners on it, I can't seem to get both tuners recognized seperately.  So when i watch TV sometimes its works properly and I see only one picture full screen, most of the time I get a split screen (top / bottom) picture. Sometimes they are crystal clear, other times the graphics are screwed up.

3. The IR port isn't recognized (built into the FusionHDTV7 card.

I just built the system last night, so I haven't had an opportunity to really mess with the system, I'll try to do that tonight.

Thanks,
DC

---

### Post by Bobber47 on 2008-12-14
I've got the same issue here.  Maybe there's hope in our numbers.

My system:
Dell Inspiron 530n
Mythbuntu 8.10
Hauppauge 1600 HVR
Saphire ATI Radeon HD 3650 w/512MB PCIe

Everything works perfectly except for the Mythbuntu frontend, where resolution errors yield the diagonal banding described above.  The backend configuration screen had the same glitch once, but was OK after that.  Note that other video displays are fine: desktop, DVDs (Xine) or online video (flash +/- full screen) are all clear and smooth without errors.  Given the Mythbuntu-specific problem, I'm uncertain if the error is with the ATI driver, though as noted, the problems don't occur with the OS driver.  For 1080p multimedia, though, acceleration is extremely helpful, so I hope someone fixes the error whether with Mythbuntu or ATI. I'm experimenting in the meantime...

---

### Post by onehotcutey on 2008-12-14
So I finally got this working.  It is the ATI driver and the fix really is just temporary.  I found the fix on another board.

---
Temporary fix for me is this:
mythfrontend > TV Settings > Playback > Next > Next (i.e. Playback Profiles (3/9))
Changed "Current Video Playback Profile" to "CPU++"
"if rez > 0 0 -> ffmpeg & XVideo" > Edit
Change "Decoder" from "Standard" to "libmpeg2"
Change "Max CPUs" from "1" to "4"
Keep pressing Next/Finish until your back into the main menu screen
----

I'm not sure what new challenges will appear with these changes, but we'll see.  I'll keep working on a true fix.

Daniel

---

### Post by Bobber47 on 2008-12-15
Great...or so I thought.  I anxiously tried what you described, hoping I'd get usable performance, but only achieved corruption of my system.
Sequence:
1 ) made Mythbuntu frontend changes you mentioned 
2 ) viewed TV: was OK (still open-source driver)
3 ) enabled Restricted driver from manager (Ubuntu distributed version, not 12/10 release from ATI)
4 ) rebooted
5 ) boot failure: monitor reports unsupported mode, ? due to autostart of Mythbuntu FE ?
6 ) forced shutdown, started in recovery mode (reset Xorg to open-source driver, finished boot); got to desktop OK with open-source driver
7 ) removed Mythbuntu from autostart list, re-enabled ATI driver, rebooted 
8 ) boot failure persists - can't get to desktop with ATI driver (always worked with activate/deactivate before when testing system...)
9 ) repeated step 6
10  removed Ubuntu-distributed ATI driver, tried installing 12/10 ATI-released driver
11 ) similar results causing repeat of step 6 with each attempt
12 ) made sure to use uninstall scripts from ATI for recent driver, all components appeared to be gone
13 ) retried Ubuntu-distributed driver, but still unable to get to desktop: now rather than "unsupported mode" report on monitor, Pop-ups report PCS database errors and lack of init screens (?)
14 ) repeated step 6 with each failure...reboots now >20
15 ) reverted to open-source driver

So now rather than only Mythbuntu frontend not working with the ATI drivers, my whole system crashes if they are enabled (whereas the desktop had been fine).  I presume some error was introduced at some step (probably #5) that isn't properly resolved by an uninstall/reinstall cycle (much like a Windows headache).  I'm dreading the solution of wiping my system and starting over again from scratch, so if you can offer any advice I'd appreciate it.

Thanks, Bob

PS. I found that Xine stopped working and X server errors are reported, even with the open-source driver.  So am I correct in assuming my Xorg config corruption is the likely culprit?  Perhaps if I could clear that I'd have success with the above solution...  Hopefully the corruption wasn't related to the changes.  How do I fix my Xorg config?  Hmm...

---

