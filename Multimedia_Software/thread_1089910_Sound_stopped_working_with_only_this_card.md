---
title: "Sound stopped working with only this card"
date: 2009-03-07
forum: Multimedia Software
---

### Post by superwad on 2009-03-07
OK, so here is my situation.  I have had sound working with this card before (SB Audigy2 ZS).  I then had to do some fixing with my hard drives, which amounted to mounting a few drives and removing a file (Windows virus), and flashing the firmware on my Seagate 1TB.  During all this, I didn't notice if the sound was working, but I likely didn't have my speakers connected.  While I was inside the machine, I bumped the sound card, but there appears to be no damage to either slot nor card.

So, after I finish my changes, I boot back into my system and notice that sound isn't working.  I check alsamixer to make sure it's not muted, double check that my speakers are connected properly.  Everything checks out.

So I take another sound card (Creative CT4810) and put it into my system (removing the Audigy2).  After booting, the sound system does a few checks, but starts playing sound again.  It prompts me to remove the Audigy2 devices, which I accept.  This replacement sound card is plugged into the exact same slot as the Audigy2.

So I take my Audigy2 and put it into another computer (Debian).  Sound starts working immediately.  Being very confused, I take my Audigy2 and put it back into its original configuration.  The sound system again prompts to remove the CT4810 devices, which I accept.  The sound still does not work.

Thinking it might be a problem with the card and the slot, I change slots the Audigy2 is using.  No change.

The only other thing that happened before this problem is that I upgraded to KDE 4.2.1.  I don't know if these two events are related.  I've checked and double checked all I can think of.  Can anybody offer any assistance?  I'd really like to continue using my Audigy2.

Much thanks.

---

### Post by markbuntu on 2009-03-09
For some reason the driver for the Audigy installs with digital output on. This disables the analog output. There should be a analog/digital switch in the volume control which needs to be unchecked.

---

### Post by superwad on 2009-03-09
I've looked, and I can't find this option.  Is this within alsamixer or KMix or some other application?  In any case, that might explain why the sound isn't working now, but why would it have stopped working after changing the hard drives?

In any case, what happened before is likely not relevant to what's going on now.  If I can figure out how to get the sound working again, I'd be happy.

So I just need to know where this switch is located, then I can check the setting, and we can go from there.

Thanks!

---

### Post by markbuntu on 2009-03-10
The switch should be in the alsamixer.
Another thing you can try is to install the audigy card and then remove/purge alsa and reinstall it. reboot and everything should work better. Some old incompatible configs may be hanging around making your life hell and the purge will get rid of them

```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```


Packages gdm and ubuntu-desktop are also removed in this process if you are also using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

``` 

Don't forget to reboot.

---

### Post by jward3010 on 2009-03-10
> **markbuntu said:**
> For some reason the driver for the Audigy installs with digital output on. This disables the analog output. There should be a analog/digital switch in the volume control which needs to be unchecked.

This fixed it for me! Thanks for that. I'm using Ubuntu 8.10 Intrepid with an Audigy 2ZS. It looks like a certain update of sound related software / drivers is causing this, read below...

In Ubuntu I went into the "Volume Control" (right-click on speaker icon in top right and select "Open Volume Control"), the device was "Audigy 2ZS (SBXXXX) Alsa mixer" and I selected "Switches" tab and unticked "Audigy Analog / Digital Output Jack", closed the volume control and sound blasted from my speakers. Success.

A certain update cycle obviously installed newer sound related updates and switched on this switch, thankfully for me it had nothing to do with hardware problems as I also have XP installed on the machine and sound worked fine in there. How I knew it was updates was by reinstalling Ubuntu 8.10 and testing sound before installing the 263 or so updates you have to do at the moment. Sound worked fine before updates, then I updated and it was gone.

---

### Post by superwad on 2009-03-10
Well, I found the checkbox that you were talking about.  It wasn't checked.  However, reinstalling alsa seemed to resolve my issue totally.

I give to you 1 internet.  You may also reward yourself as you see fit.

Thanks greatly sir!

---

