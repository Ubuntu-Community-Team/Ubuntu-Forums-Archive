---
title: "no sound at all in hardy"
date: 2008-09-06
forum: Multimedia Software
---

### Post by velozoom on 2008-09-06
Fresh install of Hardy from a cd this evening.  My system is getting a bit old but can't imagine it's not supported-

Asus KV8 5E deluxe mobo
AMD Athlon 64 3200+ 
1.5 Gb RAM

Sound card is a +3 year old SBLive PCI 4.1 

Only kernel image installed is 2.6.24-21-generic

I've been googling this issue for about 2 hours and am going in circles.  Every solution I've read about has failed.  

I've uninstalled all kernels but the most recent, opened my repositories to third party and pre-release software, et al, installed module-assistant to rebuild the alsa module.....

Need some help here, not even sure where to start looking at this point.  What should I be looking at?  

Thanks.....

---

### Post by doas777 on 2008-09-06
does the sound card show up in lshw and lspci ?
```
lshw
```
```
lspci
```

---

### Post by overdrank on 2008-09-06
Moved :)

---

### Post by velozoom on 2008-09-06
Output of lshw-
```
 *-multimedia:0
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1

```

Output of lspci
```
00:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)

```

Also, when I set the sound in system>preferences>sound to use "multichannel playback" I can hear the test tone out of my speakers but it appears no actual sound data is being sent to the card from any other application.  No startup or shutdown sounds.  For a while I was getting sound out of the MoBo speaker but no longer...

---

### Post by velozoom on 2008-09-06
couple more things I tired based on other threads here- 

removed pulseaudio and installed the alsa lib to no effect.
set all sounds output devices to alsa and disabled system sounds...nada

at this point I'm clueless.  Thanks for any help....

---

### Post by velozoom on 2008-09-06
After more and more digging I stumbled on the solution.  Completely removed pulseaudio and alsa.  Installed OSS and recreated the OSS libflashsupport and I have sound.

---

