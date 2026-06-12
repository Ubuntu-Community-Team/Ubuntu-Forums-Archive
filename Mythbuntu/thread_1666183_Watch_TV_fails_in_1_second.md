---
title: "Watch TV fails in 1 second"
date: 2011-01-13
forum: Mythbuntu
---

### Post by Twig E. Pottox on 2011-01-13
Fresh install of Mythbuntu 10.10 on dual boot machine with win 7 on separate HDD.  Silicon Dust HD - 2 , Broadcast over air ATSC (US)  AMDX4 6000 n-vidia 9800 FE/BE on one PC for now.

Mythbuntu starts from log on screen and brings up the menu with no problem. when I select Watch TV it says wait then in a few seconds the off air schedule appears with the local channels  and off air program info ok. However this screen only stays up for a second or two then it goes blank and reverts to the log on screen requiring my password to log on. I could go in circles all day!

I installed and setup following a how-to from the forum.  Apparently I got the channels to scan ok and it is pulling program info off air as well. What could be making it crash?? The only part I could get working was the weather section.

Hate to admit that the tuner is working relatively well with media center on the win 7 side... only the rare BSOD!!

This is my fifth attempt to install myth over the last couple of years with no success.  I bought the silicon dust unit after compatibility problems with other tuner cards. cant say I haven't tried. I would greatly appreciate some advice or being pointed in the direction where I could find a fix for this problem. Thanks in advance for any help.

---

### Post by iamlindoro on 2011-01-13
> **Twig E. Pottox said:**
> Fresh install of Mythbuntu 10.10 on dual boot machine with win 7 on separate HDD.  Silicon Dust HD - 2 , Broadcast over air ATSC (US)  AMDX4 6000 n-vidia 9800 FE/BE on one PC for now.

Mythbuntu starts from log on screen and brings up the menu with no problem. when I select Watch TV it says wait then in a few seconds the off air schedule appears with the local channels  and off air program info ok. However this screen only stays up for a second or two then it goes blank and reverts to the log on screen requiring my password to log on. I could go in circles all day!

You are experiencing a bug in xorg, not in MythTV.  Unfortunately Xorg advertises XvMC as available and when MythTv tries to access it, X crashes.  Whoops.

You can work around it in MythTV, however.

Utilities/Setup->Setup->TV Settings->Playback Settings, Page Three.  You are likely on the "CPU+" playback profile right now.  Switch the profile to "Slim" (or you could also choose "VDPAU Normal" based on your GPU hardware).  Then click next until you see finish, then hit finish.  Now try watching TV again.

---

### Post by Twig E. Pottox on 2011-01-13
Problem solved

Its Magic, that did the trick.  xorg takes some getting used to.

thanks again for your hepl

---

