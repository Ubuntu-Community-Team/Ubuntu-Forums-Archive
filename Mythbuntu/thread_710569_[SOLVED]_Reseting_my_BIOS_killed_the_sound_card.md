---
title: "[SOLVED] Reseting my BIOS killed the sound card"
date: 2008-02-28
forum: Mythbuntu
---

### Post by Caps18 on 2008-02-28
I'm not sure if there is some BIOS setting that needs to be set correctly, but I can't seem to find anything wrong there.

With a terminal, I can type ' lspci -v ' and it finds the sound card.  It also thinks my two pcHDTV5500 tuners are sound cards as well, but I'm not sure if it matters.  ' alsamixer ' when run from the command line started with one of them.  I had to use ' alsamixer -c2 ' to get the sound card controls to come up.

But when I try to play something in mplayer, I get the error " Could not open/initialize audio device -> no sound ".  Anybody have any ideas of what I can do or try to get this working?

The sound card had been working fine prior to this.

-----------------

[UPDATE]
Before I even posted this, but after spending 4 hours figuring it out.  I think I can explain what happened.  When I first setup Mythbbuntu, I only had the sound card and a TV tuner.  Then I added another TV tuner.  Next I reset my BIOS, which caused the soundcard to go from dsp0 to dsp2.  At least that is what I think happened.  Now that I have it setup correctly in MythTV, the sound works again.

I will have to test mplayer again, because I still couldn't play any videos from mythvideo.

---

### Post by Caps18 on 2008-03-01
I have to use Xine now for my internal player.  It does a better job with my mkv files anyway.

---

