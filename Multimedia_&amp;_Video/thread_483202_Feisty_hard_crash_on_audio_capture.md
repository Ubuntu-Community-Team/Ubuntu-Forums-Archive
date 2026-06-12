---
title: "Feisty hard crash on audio capture"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by atfrase on 2007-06-24
Every time I try to record audio (into any application, from any input source), my machine locks up ~5s later.  Ctrl-Alt-F# does not respond, Alt-SysRq-S/U/B does not respond, I have to completely power-down and power-up again.

Initially this was happening with my onboard audio chip (via82xx), which i have now disabled and installed a SoundBlaster Live! Value PCI card (emu10k1) with exactly the same results.  I can play audio just fine (from multiple applications simultaneously, even), but as soon as I try to record, the system locks up ~5s later, even if I stop the recording before that point.

I've tried captures from line-in and mic, into GNUsound, Audacity, Sound Recorder and Ventrilo(wine), with the same result.  When recording from mic in GNUsound, I can see the waveform as it is being captured and it matches my input, so the signal IS being received and captured -- until the system locks up.

I tried everything in the 'Comprehensive Sound Problem' guide including --purge and re-install of all ALSA modules, to no avail.  I also tried recompiling the driver for just my emu10k1 sound chip (both from the standard Ubuntu source package and bleeding-edge source from alsa-project), but both compiles failed (errors in include/linux/pci.h).

The computer is a freshly assembled machine in the last week:
ASUS M2N32-SLI Deluxe; AMD X2 6000+; nVidia 8800 GTS PCIe; SoundBlaster Live! Value PCI; 2gb Corsair DDR2-800 RAM.  Memory and hard drive both tested OK before I even installed Ubuntu.

I am a fresh migrant from WinXP and have been impressed so far with Ubuntu, but this problem is really testing my patience; full duplex audio should 'just work'.  I can maybe forgive the onboard chip having issues, its a pretty new mainboard and onboard sound is always a tad iffy, but a 5+ year old PCI SoundBlaster really should be flawless out of the box.

Any ideas?

---

### Post by atfrase on 2007-06-25
Alright, update -- the hard crash turns out to have been related somehow to my mainboard's onboard wireless adapter (which is really USB wireless, it plugs into a USB header).  I'm not using wireless anyway, and as soon as I blacklisted its driver (rtl8187), I no longer get a total system freeze when I try to record.

What I DO get, however, is an X server crash.  And it's not delayed anymore, either; as soon as I press record, the mouse stutters for a second and then my entire X session (on both monitors, which are configured as separate displays) dies and I have to log in again.

I don't even know where to look for debugging info, if there is any.  I tried /var/log/Xorg.0.log and dmesg and didn't see any clues.

From googling, it seems like a *LOT* of people have problems recording audio in Ubuntu.  What's the deal?

---

### Post by pablo88 on 2007-06-28
I too have a problem. In fact, Ive never been able to record a thing via Audacity. The onboard laptop mic and a plug in headset mic both fail. This makes the use of skype, gizmo, sipphone etc not possible. So any solutions you find I would be more than interested in.

-- Pablo

---

