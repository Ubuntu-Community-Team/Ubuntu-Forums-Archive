---
title: "Best Ubuntu-Compatible PCI-E Sound Card"
date: 2009-12-21
forum: Multimedia Software
---

### Post by erixoltan on 2009-12-21
Does anyone know some PCI-Express sound cards that are guaranteed to work well in Ubuntu?  (I have a 64 bit Karmic 9.10 system.)  

I am throwing away the SoundBlaster X-Fi Xtreme Audio sound card that came with my new computer because I just can't get it to work.  I will have an empty PCI-E slot where I'd like to plug in something that will work well.  

If I'm going to spend money on a soundcard I want to make sure that it works with Linux.  Any advice would be greatly appreciated.  

Thanks,
Erik

---

### Post by Yellow Pasque on 2009-12-21
> I am throwing away the SoundBlaster X-Fi Xtreme Audio sound card that came with my new computer because I just can't get it to work.

You're not literally throwing it away, right?

---

### Post by erixoltan on 2009-12-22
> **Temüjin said:**
> You're not literally throwing it away, right?
LOL no, not literally.  I figure eventually the Linux kernel will support it and I can put it back in.  Right now I can't get any sound at all in Linux.  

Hey this is a **big opportunity**.  If anyone has an axe to grind about which is the best soundcard in Ubuntu (or even a good one), then here is your chance!  

Some good soundcards don't sound great in Linux because of badly-written drivers.  (At this point inferior sound would be a step up....)

---

### Post by VertexPusher on 2009-12-22
> **erixoltan said:**
> Any advice would be greatly appreciated.
Use onboard sound.

Seriously. The days when dedicated sound cards made a huge difference are over. AC'97 is gone. If your mainboard is less than 4 years old, it probably has a built-in HDA adapter capable of 24bit dynamic range and 96kHz sample rate. Finally, if you are unhappy with the default sample rate converter, configure ALSA to use a better one (in ~/.asoundrc):
```
defaults.pcm.rate_converter "samplerate_best"
```

---

### Post by erixoltan on 2009-12-22
> **VertexPusher said:**
> Use onboard sound.

Seriously. The days when dedicated sound cards made a huge difference are over. AC'97 is gone. If your mainboard is less than 4 years old, it probably has a built-in HDA adapter capable of 24bit dynamic range and 96kHz sample rate. Finally, if you are unhappy with the default sample rate converter, configure ALSA to use a better one (in ~/.asoundrc):
```
defaults.pcm.rate_converter "samplerate_best"
```
Well, there _IS_ a little plastic cover marked **DO NOT REMOVE** and when I _remove_ it (LOL) it shows some jacks underneath.  I suppose there's probably (??) a jumper on the board somewhere that I can change to re-enable the onboard sound.  

Hmm.  The computer is only a few weeks old, how bad can the sound actually *be*?  

I will take a look and post back here.

---

### Post by erixoltan on 2009-12-22
All I had to do was to remove the sound card.  I put in an Ubuntu disk and rebooted, and I heard the ubuntu startup sound.  Sounds pretty good too.  I am reformatting as I type this and eliminating Windows 7 from my life, since this was the last obstacle.  

Thanks for the tip!!! I am marking this resolved.

---

### Post by Yellow Pasque on 2009-12-22
If you ever want to try the X-fi again, [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by erixoltan on 2009-12-23
Thanks.  I did try that but had no luck with it.  

I am sure that in time the sound card will just work on a clean Ubuntu install -- I do intend to try again in a year or so.

---

### Post by jgatkinsn on 2009-12-24
I can't say that I would recommend going back to onboard audio if you have an Intel HDA (Realtek) audio chipset.  I'm having heck of a time trying to get my sound to work reliably in the past three versions of kubuntu and two motherboards, to the point of pulling my hair out and wanting to put WinDoze back on the system.   I'm actually looking for a card that works 100% all the time in Linux and stays working.  

I can usually get sound working for a while, but after some time it quits working until I shutdown as wally as Mozilla audio quits working in flash.  Annoying.

---

### Post by thomaszmark on 2009-12-24
I have seen your link with good sound card, tks

---

