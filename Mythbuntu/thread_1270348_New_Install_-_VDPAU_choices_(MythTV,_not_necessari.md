---
title: "New Install - VDPAU choices (MythTV, not necessarily Mythbuntu)"
date: 2009-09-19
forum: Mythbuntu
---

### Post by yonkiman on 2009-09-19
I've been running Mythbuntu 8.04 since its release.  I also have an Ubuntu (not Mythbuntu) 9.04 system on the same hardware that I'd like to bring Myth up on (front and back ends).

So it seems I have several choices how to proceed:
[LIST=1]
[*]JAvenard's 0.21 distribution.  This is probably the safest way to get VDPAU support.  But it's MythTV 0.21, and I will admit to being 0.22-curious...
[*]0.22 trunk.  I don't feel like I know enough about this.  It's been in development for a while and hear it's converging towards a release version.  I'm happy to accept some risk (and learn how to report bugs, etc.) to help the development.  But I'd like to get some idea of the level of risk.  GUI and some playback glitches would be fine - database corruption would not (though I suppose I could automate database backups, so maybe I could live with that, too).  I've also yet to see clear instructions on how to install it from scratch (do I need to install 0.21 and upgrade, how do I "switch" from 0.21 to 0.21 + 0.22 changes, etc.?).
[*]Mythbuntu 9.04.  No VDPAU support and I'd have to reinstall my 9.04 system, so not interested.
[*]Mythbuntu 9.10 trunk?  Is this an option?  Is the Myth version 0.21 or 0.22?  I'd be willing to lose my 9.04 install and support Mythbuntu 9.10 development if it supports 0.22.
[/LIST]

I'm clearly leaning towards #2, but I'd appreciate any thoughts/opinions on which way to proceed before I pull the trigger!

---

### Post by tgm4883 on 2009-09-19
> **yonkiman said:**
> I've been running Mythbuntu 8.04 since its release.  I also have an Ubuntu (not Mythbuntu) 9.04 system on the same hardware that I'd like to bring Myth up on (front and back ends).

So it seems I have several choices how to proceed:
[LIST=1]
[*]JAvenard's 0.21 distribution.  This is probably the safest way to get VDPAU support.  But it's MythTV 0.21, and I will admit to being 0.22-curious...
[*]0.22 trunk.  I don't feel like I know enough about this.  It's been in development for a while and hear it's converging towards a release version.  I'm happy to accept some risk (and learn how to report bugs, etc.) to help the development.  But I'd like to get some idea of the level of risk.  GUI and some playback glitches would be fine - database corruption would not (though I suppose I could automate database backups, so maybe I could live with that, too).  I've also yet to see clear instructions on how to install it from scratch (do I need to install 0.21 and upgrade, how do I "switch" from 0.21 to 0.21 + 0.22 changes, etc.?).
[*]Mythbuntu 9.04.  No VDPAU support and I'd have to reinstall my 9.04 system, so not interested.
[*]Mythbuntu 9.10 trunk?  Is this an option?  Is the Myth version 0.21 or 0.22?  I'd be willing to lose my 9.04 install and support Mythbuntu 9.10 development if it supports 0.22.
[/LIST]

I'm clearly leaning towards #2, but I'd appreciate any thoughts/opinions on which way to proceed before I pull the trigger!

Enable the trunk (0.22) weekly repo.  [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by yonkiman on 2009-09-19
> **tgm4883 said:**
> Enable the trunk (0.22) weekly repo.  [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

Thanks for the suggestion, but I still have a few questions:
[LIST]
[*] What's the difference between mythbuntu trunk and mythtv trunk?
[*] Can I add either to an existing 9.04 system?
[/LIST]

---

### Post by mrand on 2009-09-19
> **yonkiman said:**
> Thanks for the suggestion, but I still have a few questions:
[LIST]
[*] What's the difference between mythbuntu trunk and mythtv trunk?
[*] Can I add either to an existing 9.04 system?
[/LIST]
Mythbuntu "trunk" is following mythtv trunk... so it lags it by a day or two - but otherwise there is no major difference except that you get the benefit of not having to compile it yourself (option #2).

Yes, I believe you can add either to a 9.04 system.  9.10 is focused on 0.22 though, so you'll get better support and stuff.

If you don't have to subject yourself to an upgrade, I'd definitely install 9.10 so that you have the latest kernel.  The decision about compiling your own mythtv source, or running mythbuntu is a separate question.

[INDENT]Marc[/INDENT]

---

### Post by yonkiman on 2009-09-19
> **mrand said:**
> If you don't have to subject yourself to an upgrade, I'd definitely install 9.10 so that you have the latest kernel.  The decision about compiling your own mythtv source, or running mythbuntu is a separate question.

OK, so I think I'd like to go with 9.10 and mythbuntu trunk (don't want to deal with compiling if I don't have to).  What are my next steps?  

It looks like I can pretty easily update the system to the latest 9.10 using update manager.  Once I do that, exactly what do I do to get connected to the 0.22 mythbuntu trunk?  I currently do not have myth installed at all.

Or do I need to just start over with the latest mythbuntu 9.10 installer?  I'd rather not lose all the effort I put in configuring and optimizing 9.04 if I can avoid it, but I will if it means a more stable base moving forward.

Thanks for the advice!

---

### Post by tgm4883 on 2009-09-19
Actually, the trunk repo now follows the 0.22 branch, not trunk. The renaming isn't going to happen though. Take a look at the link I posted above.

---

### Post by yonkiman on 2009-09-20
OK, I seem to be there!
[LIST]
[*]Updated 9.04 to 9.10 with instructions from [http://www.ubuntu.com/testing/karmic/alpha6](http://www.ubuntu.com/testing/karmic/alpha6)  (press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box)
[*]Added 0.22 trunk per tgm4883's answer ([http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds))
[/LIST]

Thanks for the support Marc and tgm4883!

---

### Post by jyavenard on 2009-09-20
> **tgm4883 said:**
> Actually, the trunk repo now follows the 0.22 branch, not trunk. The renaming isn't going to happen though. Take a look at the link I posted above.

This is a bad move.

It was decided that that 0.22 branch had been created too early and isn't going to be updated.

Instead a new branch will be created from trunk when the fixes are starting to settle...

You should continue to follow trunk for now..

Edit: I build daily trunk packages in my "trunk" repository (Jaunty / Intrepid only).
deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) jaunty trunk

It includes some extra code I wanted to have in trunk, but miss the dead line (like the new audio configuration and code)...

---

### Post by yonkiman on 2009-09-20
> **jyavenard said:**
> This is a bad move....You should continue to follow trunk for now..

So right now the repository I'm using is this one: 
[http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu](http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu)

Is that the "abandoned" branch or am I on the right one?

I'm 64 bit Koala now (though again, I could start all over if what I've done so far is build a mess) - is there a trunk you'd recommend or do you think I should stick to Jaunty for now?  My goal is to build a stable VDPAU system with a future!

This whole discussion is just a *little* beyond my complete understanding, so I appreciate all the help!  :-)

---

### Post by jyavenard on 2009-09-20
> **yonkiman said:**
> So right now the repository I'm using is this one: 
[http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu](http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu)

Is that the "abandoned" branch or am I on the right one?

I'm 64 bit Koala now (though again, I could start all over if what I've done so far is build a mess) - is there a trunk you'd recommend or do you think I should stick to Jaunty for now?  My goal is to build a stable VDPAU system with a future!

This whole discussion is just a *little* beyond my complete understanding, so I appreciate all the help!  :-)

The only advantage for Myth users with Koala, is that it will bring DVB-S2 support which comes with 2.6.30 kernels and newer.

Other than that, there aren't really any reasons to upgrade from Jaunty yet ...
Actually, Koala ships with nvidia driver 185.xx ; which in my experience suck stability-wise with VDPAU. When using 185.x, I suffer daily lock up or crash. And I can make the drivers crash in about 10s using vdpau in some special circumstances.
Sticking with 180.60 for the time being is better.


I don't know what branch mythbuntu weekly is using, but right now the branch even got deleted from MythTV SVN...

If you're after stability, currently 0.21-fixes with my VDPAU backport is more stable/usable than trunk.

Jean-Yves

---

### Post by orduek on 2009-10-08
when do you think it will be worthwhile to move to the 0.22?
I'm currently using 8.10 with your 0.21fixes but I had to add XBMC button to manage all my media library.
I think 0.22 will manage the video libraries much better than the 0.21.

---

