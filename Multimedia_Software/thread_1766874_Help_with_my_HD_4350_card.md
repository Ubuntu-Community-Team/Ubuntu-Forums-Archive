---
title: "Help with my HD 4350 card"
date: 2011-05-24
forum: Multimedia Software
---

### Post by jeliocranch on 2011-05-24
Hi, 
Hoping someone can help me with an odd video card issue, or driver issue, or something.
I've had a quasi-htpc setup for some time now, using a foxconn mobu, Powercolor HD-4350 video card with 512MB on board, and a dual core AMD processor of some flavor, ranging from 1.8 to 2.7 GHz.  It has been running Windows 7 32 bit, but the windows interface is horrible for htpc, and this was the last machine to make the migration to Linux.  
Recently installed Natty, currently dual booting.  I've done the ati driver download, but watching video is, well its not video.  Its stills with an audio track.  Doesn't matter the compression level: full Blue-Ray HD to 700MB highly compressed.
I've got another AMD dual core with low-end onboard Nvidia, which plays lower-def videos great running Natty, and an AMD quad core machine with a 4850 card running Natty and playing videos just fine.
I started thinking the card was overheating (is passively cooled) so I put a fan on it.  The heatsink is only mildly warm, but still the video is choppy at best and still images at worst.  Maybe the card went bad, I thought.
Like I said, its a dual boot and I wasn't having this problem with Windows, so I booted back into 7, and its perfect. Grrr. 
Since installing Natty, I have overclocked the machine.  Thinking it was an OC thing, I turned everything back down to no effect.
I know I've missed something, but don't know what.
Here are my known differences:
This machine was a fresh install of Natty, the others were software upgrades from Maverick. 
The ATI driver on the quad core was installed and activated while in Maverick.
Please help!  I'm so close to cutting ties with Microsoft...  This is the final string.:confused:

---

### Post by jeliocranch on 2011-05-25
I thought of another difference, the misbehaving machine is running 32 bit ubuntu, while the quad core is 64 bit.

---

### Post by jeliocranch on 2011-05-25
Switching Back to Windows 7 definitely sorted the issue.  extra Grrr.  Removed FGLRX driver and installed the new one from ATI (released 5/9/11) and same choppy/freezyness.

I tried a little experiment with the 64 bit Natty machine: I turned off 2 cores and underclocked it to 2.4 GHz, 2200 MHz NB, 2000 MHz HT, 800 MHz ram with slightly slower timings than are on the dual core, but otherwise virtually identical setups.  The two machines even have the same HDD's (WD Caviar blacks, 640 GB).  Then I moved the video card over from the misbehaving 32 bit machine to the 64 Bit machine.  Perfect video.
System monitor shows an average of about 50-60% CPU usage, just under 1GB of ram used, no swap.

Next, I'm going to try running the HDD from the 32 bit on the other machine, and vice versa.  I'm really starting to think its a bug in 32 bit Natty......

---

