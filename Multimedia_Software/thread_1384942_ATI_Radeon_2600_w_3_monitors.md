---
title: "ATI Radeon 2600 w 3 monitors?"
date: 2010-01-19
forum: Multimedia Software
---

### Post by starsprout on 2010-01-19
Hi-

I fianally borke and put Ubuntu on my desktop. I was running Winxp before and have this nifty Radeon ATI 2600 card that enabled my 3-monitor layout, but no more.

At the Ati website I found the driver and installed it and went through every step in the installation notes sucessfully, but I've still got 3 monitors and only 2 of them receiving signal from the graphics card no matter how I configure their physical plugins.

Anyone running a 3 monitor setup with this card or know any other info about getting this $500 card to work in ubuntu?

---

### Post by merrak on 2010-01-26
> **starsprout said:**
> Hi-

I fianally borke and put Ubuntu on my desktop. I was running Winxp before and have this nifty Radeon ATI 2600 card that enabled my 3-monitor layout, but no more.

At the Ati website I found the driver and installed it and went through every step in the installation notes sucessfully, but I've still got 3 monitors and only 2 of them receiving signal from the graphics card no matter how I configure their physical plugins.

Anyone running a 3 monitor setup with this card or know any other info about getting this $500 card to work in ubuntu?

I have a three monitor setup with two ATI cards (HD 4350 and 4550) with two monitors plugged into the 4550 and one into the 4350. The two attached to the 4550 form one big desktop - but the one attached to the 4350 is in a separate X session. I don't know if this is what you're going for (usually people one want big desktop, but in this case this was the desired outcome). I can share my xorg.conf if this is what you're shooting for. Perhaps it'd help. If you're looking for one big desktop, have you come across this thread yet?

[http://ubuntuforums.org/showthread.php?t=1046527&page=2](http://ubuntuforums.org/showthread.php?t=1046527&page=2)

Near the bottom he has success getting all three to work.

---

### Post by starsprout on 2010-02-11
> **merrak said:**
> I have a three monitor setup with two ATI cards (HD 4350 and 4550) with two monitors plugged into the 4550 and one into the 4350.

[http://ubuntuforums.org/showthread.php?t=1046527&page=2](http://ubuntuforums.org/showthread.php?t=1046527&page=2)



> **merrak said:**
> I have a three monitor setup with two ATI cards (HD 4350 and 4550) with two monitors plugged into the 4550 and one into the 4350.

Yeah but what if I have just one pci card? I even gave up on three monitors and am just running 2 at the moment, but not optimally by any means.

My friend says xrandr is what I need. But I know very little about it. He says "X" is a long-term evolving project. Is xrandr part of that? I checked out the thread in the link above but it also seems to be dealing with multiple cards' setup

I can go to Display Preferences and set some things, but graphics like compiz or cairo-dock don't run like they did on the proprietary drivers I tried for a while before the  endless crashes.

What's the best way to configure my Radeon 2600 card? What is xrandr?

---

