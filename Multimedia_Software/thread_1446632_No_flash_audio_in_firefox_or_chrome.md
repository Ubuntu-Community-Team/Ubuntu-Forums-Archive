---
title: "No flash audio in firefox or chrome"
date: 2010-04-04
forum: Multimedia Software
---

### Post by jimbo12345 on 2010-04-04
Hi

Im using ubuntu 9.10, and overall rather impressed, however can't get no sound in flash through firefox or chrome...  I've been searching through forums for the past 3 days trying to fix it and have tried just about every fix that I can find.  All other audio is absolutely fine, music plays, video's play, but no audio from flash apps.  So far i've removed and reinsalled various flash plugins (nonfree/adobe etc...)  reinstalled pulseaudio.  removed pulse.  Installed ESD. removed ESD, reinstalled pulseaudio.  i've tried all sorts, and nothing has changed.  I know it has worked before, after i'd first installed, but i've only had it installed for a week, and so far i've done nothing with it apart from setup my Email clients and customise the desktop and visuals, so i can't really see why this would affect the flash player.

Anyone any idea's at all before I remove it all and go back to windows?

---

### Post by stderr on 2010-04-04
Hello jimbo12345,

Yes, there are issues with flash and sound through Pulseaudio... however you should be able to resolve them pretty simply.

Ensure that pulseaudio is installed & running (reboot if necessary), and that you've got the official nonfree flashplugin installed, and that it's working (other than for sound).

Then install the extrasound package:

```
sudo apt-get install flashplugin-nonfree-extrasound
```

Finally, restart Firefox. 

HTH

---

### Post by jimbo12345 on 2010-04-04
Unfortunately, already tried that numerous times... i've tried it both with the flashplugin-nonfree, flashplugin-installer & flashplugin-nonfree-extrasound packages - which is how it currently is, as well as using the adobe-flashplugin, neither seem to perform any differently from eachother - as a side note, flash no longer even plays the videos, it crashes both chrome and firefox.  One thing i have noticed though, is if I completely remove flash altogether, and try to load the page in firefox, it prompts me to install flash player - however chrome continues to work - or tries to play the video, even though no flash plugins are installed in synaptic, indicating maybe chrome is using its own plugin.... maybe?   I don't know enough about linux to figure it out...

I'm good with computers, but new to Linux so it's a bit over my head, but i can't understand how it has stopped working from one day to the next, i was on youtube & bbc's Iplayer no problem the other night.  Now no sound!

I'd like to get it sorted rather than resort to wiping it and starting again, as i've finally configured my music, vids,  hardware & everything else to work the way I like, just seems like a bit of an **** to have to reboot into windows to catch up on the days TV online....

---

### Post by jimbo12345 on 2010-04-04
ok, i've found out that by booting into the Ubuntu trial from the CD, i can get sound from firefox after installing the .deb from flash's site for ubuntu 8.04+.  I've also tried this package on my install but with no joy, indicating maybe the problem isn't with flash but elsewhere within my system configuration - the question is where...?  or how do I replicate the sound settings from this trial back onto my full install??  As i say on my install all sound is absolutely fine apart from within web browsers....   

I'm currently in the process of trying to match all pulseaudio & flash packages like for like between this trial version & my installed version to see if that resolves things...

---

### Post by lovinglinux on 2010-04-04
> **jimbo12345 said:**
> ok, i've found out that by booting into the Ubuntu trial from the CD, i can get sound from firefox after installing the .deb from flash's site for ubuntu 8.04+.  I've also tried this package on my install but with no joy, indicating maybe the problem isn't with flash but elsewhere within my system configuration - the question is where...?  or how do I replicate the sound settings from this trial back onto my full install??  As i say on my install all sound is absolutely fine apart from within web browsers....   

I'm currently in the process of trying to match all pulseaudio & flash packages like for like between this trial version & my installed version to see if that resolves things...

Are you sure the correct flash plugin is recognized by Firefox? go to about[noparse]:[/noparse]plugins in the address bar and verify the flash plugin version and file name.

---

### Post by Ububtubobl on 2010-04-05
I also tried the suggestions in the stickies without success . Finally went to Java web site and found I didn't have latest version so using the synaptic mgr in System, Administration uploaded and installed. Seems to have solved the problem.

---

### Post by jimbo12345 on 2010-04-05
I never did solve it,  I'd completely removed all instances of flash, and reinstalled all different ones from synaptic.  I also installed the one from adobe, with no joy.  I've now wiped and reinstalled the lot, and its all back to normal, after only installing the apps I really need.  I think there was some version of flash stuck in my system though, as after the rebuild I found chrome was asking for flash to be installed, yet on the faulty version, even after removing all of instances of flash from synaptic, chrome would still play flash files, only with no sound, although firefox wouldn't play at all.

I think my messing around with pulseaudio may have caused the issue, although I now have pulse installed and flash is still working

---

