---
title: "Mythtv hangs when guide is opened"
date: 2008-09-19
forum: Mythbuntu
---

### Post by false_apology on 2008-09-19
Hey all,

I finally got my mythBox setup and working!!! I'm getting ATSC signals, I'm locking channels; playback and recording are both working. There are a couple quirks that I'm trying to hammer out; and the biggest one I'm coming here for help on. 

For some reason, whenever I bring up the guide, it seems to hang and almost freeze. The mini-playback stills goes along smooth, I ssh'd in, and my CPU usage is only at like 47%. But nothing seems to happen when I push buttons (remote or keyboard, tried both). Then, probably after about 30-40 seconds, all the buttons I pressed all execute super fast one after the other. Then, back to square one; frozen/hung, etc. 

I tried switching the guide to a less cpu intensive display mode, but it didn't help. I didn't really think it would because my CPU % was not maxed out. Any ideas? Suggestions? I'm using Myth v0.21.20080304-1 on Ubuntu 8.04.1 (just burned the live CD about a week ago).

Thanks!

---

### Post by bmathis on 2008-09-19
I have the same issue but thought it was cause my processor was a P4 1.7GHz... any info on a fix would be nice.

---

### Post by laga on 2008-09-19
Please try this fix: [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/229949/comments/28](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/229949/comments/28)

and let me know if it works for you.

---

### Post by false_apology on 2008-09-19
> **laga said:**
> Please try this fix: [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/229949/comments/28](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/229949/comments/28)

and let me know if it works for you.

Sorry for the newb question but can you direct me to a tutorial on how to apply this patch? I'm a bit concerned as I just spent all week getting this working, and I don't want to break it by trying to apply a patch while not knowing what I'm doing.

Thanks

---

### Post by anonymousdog on 2008-09-19
sudo update-manager.

---

### Post by laga on 2008-09-19
Hello,

you just add ```
deb http://ppa.launchpad.net/laga/ubuntu hardy main
``` to your /etc/apt/sources.list. Then you can perform an update.

This wiki might be helpful: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Other%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Other%20Repositories)


If you're afraid of breaking your system, you can always get a backup :)

---

### Post by false_apology on 2008-09-20
I followed the directions indicated by laga, ran the update-manager, restarted, and the problem is fixed!! Thanks so much!

---

### Post by laga on 2008-09-21
Neat! Thanks for testing :)

---

### Post by CoasterCOG on 2008-09-24
Thanks a ton Laga. This issue was impacting my WAF a little since I upgraded to hardy. Your fix worked like a charm, I'm interested in what was broken though.

---

### Post by laga on 2008-09-25
> **CoasterCOG said:**
> Thanks a ton Laga. This issue was impacting my WAF a little since I upgraded to hardy. Your fix worked like a charm, I'm interested in what was broken though.

It's not a proper "fix". The bob deinterlacer was causing the high CPU load when using the guide. That workaround I backported from trunk just disables the deinterlacer when entering the guide.


I think danielk commented in the upstream bug report that the issue is fixed properly in the mythtv-vid branch, which is going to be merged back into trunk before 0.22.

I have no clue what the actual issue was, though ;)

This fix is now also in the weekly builds repository.

---

### Post by superm1 on 2008-09-25
(and intrepid for those of you who are feeling intrepid and want to upgrade :))

---

### Post by rbm0307 on 2008-09-28
> **laga said:**
> you just add ```
deb http://ppa.launchpad.net/laga/ubuntu hardy main
``` to your /etc/apt/sources.list. Then you can perform an update.
I'm experienceing the same guide hang problems with my Mythtv.  I've got a split frontend/backend setup so is this patch applied to the frontend (where the guide is displayed) or to the backend (where guide data is assembled) or both.

---

### Post by laga on 2008-09-29
> **rbm0307 said:**
> I'm experienceing the same guide hang problems with my Mythtv.  I've got a split frontend/backend setup so is this patch applied to the frontend (where the guide is displayed) or to the backend (where guide data is assembled) or both.

Frontend only. I'd recommend you try the weekly builds, they should have the same patches: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by jeworley on 2008-10-25
I have this problem too. AMD Athlon XP1800+ with an ATI 9600GT. I thought it was just hardware, but Myth runs better on my modded xbox than on this computer.

I can't make the fix above work. I'm running Xubuntu 8.04 and the latest Myth. Do I really have to take on the extra overhead of Gnome just to make Myth work?

Thanks!

---

### Post by uncle hammy on 2008-10-26
I have had the same problem for so long now, I had just kind of given up on it.  Laga, you mention your fx is in the weekly fixes builds, which I run on all my machines, yet they all experience this bug.  Am I not yet quite current enough, here's my versions as reported by apt-cache policy mythtv...

mythtv:
  Installed: 0.21.0+fixes18704-0ubuntu0+mythbuntu1
  Candidate: 0.21.0+fixes18704-0ubuntu0+mythbuntu1
  Version table:
 *** 0.21.0+fixes18704-0ubuntu0+mythbuntu1 0
        500 [http://weeklybuilds.mythbuntu.org](http://weeklybuilds.mythbuntu.org) hardy/main Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes18207-0ubuntu4~hardy1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
     0.21.0+fixes16838-0ubuntu3.1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
     0.21.0+fixes16838-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages

---

### Post by jdeslip on 2009-01-26
I am having the same problem with my hauppauge hvr 1600 in mythbuntu 0.21 weekly-builds box (mythbuntu 8.10). The problem exists even after I change to Slim or set it to a new profile with absolutely no deinterlacer at all.

---

