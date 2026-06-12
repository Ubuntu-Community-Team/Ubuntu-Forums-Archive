---
title: "Audio Card Not Recognized"
date: 2012-01-12
forum: Multimedia Software
---

### Post by Hugh Bond on 2012-01-12
My audio card (Audigy Sound Blaster) was noisy (it sounded like a scratchy record previously on Windows XP but got much worse on Ubuntu) so I bought a cheap new StarTech 4CH card.  When I put it in the PCI slot and booted up, my system ceased to acknowledge there was a sound card on board.  I swapped back to the Audigy that functioned noisily before and it wasn't recognized either.  I lived with no sound for several months, then purchased a StarTech USB sound adapter hoping for a quick, cheap fix.  It functions on my XP laptop but, like the PCI card, it's not recognized on this machine.  

The unrecognized card first occurred on 10.04 and I recently upgraded to 10.10 with the same result.  The machine is an older Dell Dimension XPS.  With both the Audigy card in the PCI slot and the USB sound adapter plugged in I get this:

~$ aplay -l
aplay: device_list:235: no soundcards found...

I read about blacklisted drivers and checked my system's blacklist.  There are some items on there that seem like they may be related but I don't know if the blacklist is unique to my system or if it's universal for each Ubuntu version.  The ones that caught my eye were:

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# replaced by p54pci
blacklist prism54

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

That last one sounded like my problem so I installed all the pulseaudio I could find with no happy result.

Am I looking in the right places?  Where should I look?

A little background on me:
I switched to Ubuntu following a HDD failure that took my XP OS with it.  With no budget for a Windows disc, I tried Ubuntu and I really like it.  While I'm technically pretty competent and not afraid to dig into this stuff, I'm not as educated on things like terminal commands and reading output as most Ubuntu users seem to be.  I hope someone can help solve this puzzle.  I searched this forum and didn't find another "no audio" post with the same "aplay: device_list:235: no soundcards found" situation.  If I missed one, please post a link for me.

---

### Post by Hugh Bond on 2012-01-12
First I'd like to say thanks to all of the 81 people who looked at this and didn't type a single keystroke.  I still don't know how the driver blacklist is compiled.

Thanks also to the mod who moved this from "General" to "Multimedia & Video."  I didn't see that section last night or else I'd have put it there in the first place.  I was also thinking maybe I should have put it into "Absolute Beginner."

I now have audio.  I got it all on my own.  I went into synaptic, searched "audio" and installed everything I could find.  That caused my PC to boot into terminal and I had no clue what to do.  The only think I could think of was to use my USB 11.10 to boot so I did and I upgraded.  That fixed it.  I lost all of my E-mail and a few programs but at least now my PC knows that there are two sound devices connected to it and sound comes out of them.  Now I'm gonna try to install classic Gnome because I saw a thread about that on here somewhere while I was looking for help.

---

