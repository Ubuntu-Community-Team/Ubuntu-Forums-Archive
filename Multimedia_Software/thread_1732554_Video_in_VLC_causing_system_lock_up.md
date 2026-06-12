---
title: "Video in VLC causing system lock up"
date: 2011-04-18
forum: Multimedia Software
---

### Post by Sylos on 2011-04-18
Hello and thanks for looking.

I have an intermittent and very irritating problem. I have a desktop PC with Ubuntu Lucid installed that I use primarily for watching films using VLC. Every so often (seemingly at random) around half way through the film the whole thing locks up - the video freezes, the audio skips (like a stuck record) and the system is unresponsive - the only cure is a full restart with the power button.

Im at a loss as to how to try and diagnose this issue. Is there a log somewhere that might have the info after I reboot?

Usefull info on the system:
- AMD processor - 64 capable but running 32 as I wanted to avoid issues.
- grpahics is via an NVIDIA Geforce FX5500 (PCI interface NOT AGP)
- Restricted NVIDIA drivers installed and working

- Also useful to note that this problem occured when using an AGP ATI Radeon 9200 (using the standard open source drivers of course). In fact the problem was worse with the ATI - the frequency of lock ups is less with the new set up.

Any insights will be gratefully received

Thanks

---

### Post by Sylos on 2011-04-19
A bump.......

---

### Post by Sylos on 2011-04-20
.....bumpety bump....

---

### Post by wkulecz on 2011-04-20
If the numlock/capslock keys won't toggle the keyboard LEDs there is not much you can do short of setting up a remote gdb session and hope it traps something you can see on the remote system before it dies.

Usually these "random" lockups are hardware issues.  If the ATI card you replaced uses more power than the current Nvidia card, IMHO its very good evidence that the powersupply should be the first thing to swap out.

Failing that, boot into memtest and let it run for a weekend.  See if you can find software to display any temperature sensor data that might be on your motherboard/CPU.

Obvioulsy if you've overclocked in any way, undo it.  Might also be useful to go re-default any BIOS performance setting you might have changed.

If you are watching in full screen mode, see if it still locks up running in a window, starting it under gdb from a terminal may leave a clue when it dies.

---

