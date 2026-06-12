---
title: "No sound in Audigy 2, only in onboard card"
date: 2010-12-12
forum: Multimedia Software
---

### Post by Mintux on 2010-12-12
I use 64-bit Ubuntu Lucid. This machine has an onboard Nvidia sound chip (which can not be disabled in BIOS), I also have an Soundblaster Audigy 2 card, which i'd rather use. 

Previously, this was impossible because Ubuntu could only configure the first card. However, with the event of 10.4 and the easy-to-use selector in Sound Preferences I was hopeful that it would work now. But no luck. Does anyone have any idea why?

I should mention that this machine dual boots to Win XP, and the Audigy works like a charm there, so it must be a Ubuntu problem. The Audigy 2 card is detected by Ubuntu, and is selectable in Sound Preferences, playback is fine with no errors, the source appears in Sound Preferences, but no sound. These are the steps I have tried, without success:

- Disable the on-board card in Sound Preferences
- Cranking all the sliders to max in Alsamixer
- Checking that there's no mute in Alsamixer, Sound Preferences, Volume Control
- Adding lines to the bottom of /etc/modprobe.d/alsa-base making the Audigy the default card (0), and the Nvidia secondary (1). The output of ```
cat /proc/asound/cards
``` now reads:

```
 0 [Audigy2        ]: Audigy2 - SB Audigy 2 [SB0240]
                      SB Audigy 2 [SB0240] (rev.4, serial:0x10071102) at 0xdc00, irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdbef8000 irq 22

```

Any suggestions?

---

### Post by lidex on 2010-12-12
> 
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.
Reference:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

---

### Post by Yellow Pasque on 2010-12-12
> **Mintux said:**
> Any suggestions?

If you're sure you don't need your onboard sound, blacklist the snd-hda-intel kernel module to prevent the driver from loading.

---

### Post by Mintux on 2010-12-18
> **lidex said:**
> Reference:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

I noticed that, however I'm not sure what kind of mixer they are referring to. There is no such checkbox in Sound Preferences, nor in Alsamixer.

In Sound Preferences the card is set to "Analog Duplex", same as the onboard card used to be. Setting it to "Digital" does not seem to make a difference.

@Temüjin: I will try blacklisting it just to make sure. I do not need the on-board card as the Audigy is better.

---

