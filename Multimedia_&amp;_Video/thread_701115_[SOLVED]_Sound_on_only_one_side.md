---
title: "[SOLVED] Sound on only one side"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by Archmage on 2008-02-19
I have only sound on one side.

I did already try the following:

Check if PCM and master volume is set for both sides, mute and unmute all, exchange speaker box, and exchange sound card.

Any help would be highly appricated.

---

### Post by Yellow Pasque on 2008-02-19
Probably would help if we knew what kind of soundcard you have, Run this:
```
sudo update-pciids; sudo lshw -C multimedia
```

---

### Post by Kingfield on 2008-02-19
And you are sure your speaker isnt broken? LOL. I know it sounds stupid but most problems like this would be caused by the speaker.

---

### Post by Archmage on 2008-02-19
> **Kingfield said:**
> And you are sure your speaker isnt broken? LOL. I know it sounds stupid but most problems like this would be caused by the speaker.

Yes, I'm sure. I did buy brand new speakers. They have the same problem. :(


@Temüjin I'll support you with the information as soon as I'm back home. But I want to point out, that I already exchange the sound card.

---

### Post by Archmage on 2008-02-19
> **Temüjin said:**
> Probably would help if we knew what kind of soundcard you have

```
  *-multimedia            
       description: Multimedia audio controller
       product: CM8738
       vendor: C-Media Electronics Inc
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2 module=snd_cmipci
```

I hope this helps. I would love to hear the sound from both speakers again.

---

### Post by Yellow Pasque on 2008-02-19
My suggestion to you is to follow the OSS4 HowTo in my signature. The C-Media 8738 chipset is supported.

---

### Post by Archmage on 2008-02-20
Trying OSS still gives me sounds only on the left  speaker. :(

---

### Post by Yellow Pasque on 2008-02-20
> **Archmage said:**
> Trying OSS still gives me sounds only on the left  speaker. :(
Then I think there's something wrong with your hardware.
EDIT: Double-check that you have everything plugged in correctly.

---

### Post by _FrEnZy_ on 2008-02-20
i have the same problem, the only working speaker is the right speaker.

here's my audio hardware..

*-multimedia            
       description: Audio device
       product: VIA High Definition Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:03:01.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
any help will be much appreciated. thank you!

---

### Post by Archmage on 2008-02-21
> **Temüjin said:**
> Then I think there's something wrong with your hardware.
EDIT: Double-check that you have everything plugged in correctly.

Thanks. In fact it was my hardware. My old speakers where broken and the new ones as well. Brand new, never used and already broken. Othere speaks work flawless.

:lolflag:

---

