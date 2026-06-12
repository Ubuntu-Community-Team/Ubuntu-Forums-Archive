---
title: "Linux compatible soundcards."
date: 2009-09-04
forum: Multimedia Software
---

### Post by xstackerx on 2009-09-04
I need to know what the best sound card is for ubuntu jaunty 9.04 amd64. I have a creative soundblaster card and ive tried following numerous forums on how to install it and i cant get it to work. If someone has an idea on what i can do let me know. I would really hate to have to buy a new one cuz this one is a good one. But i would like to know what ones would deffinately work for ubuntu. Please let me know. 
 
Thanks

---

### Post by starcraft.man on 2009-09-04
I think you'll wanna browse [here]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards").

For record, buy nothing with XFI chip unless something drastic happens, it's support is coming it seems but won't be here timely from what I seen.

---

### Post by bcschmerker on 2009-09-05
I currently use the Creative Laboratories Sound Blaster Audigy 2 ZS (Model SB0250; E-mu 10k1 chipset), which autodetected just fine in ALSA on an 8.04-LTS system running Kernel 2.6.24-24-generic.  I installed a few specific packages to support the SB0250 via Synaptic Package Manager:

From the Universe repository:
alsa-tools          Includes as10k1, an Assembler for the E-mu 10k1.
awesfx              E-mu 10k1-specific utilities.
fluid-soundfont-gm  General MIDI Sound Font, SF2 format.
fluid-soundfont-gs  Extension Sound Font to support Roland GS MIDI controls.
ld10k1              ALSA SoundFont loader.
liblo10k1-0         ALSA SoundFont support libraries.

In my case, I also installed the PulseAudio v.0.9.10-2ubuntu4~ppa3 packages as backports from 9.04, but this may not be necessary with your setup.

---

### Post by xstackerx on 2009-09-05
okay im very new to linux. i just installed it a week ago. is there any website that can walk me through how to get all the packages and software that i need?

---

### Post by pfunkman on 2009-09-05
Audigy 2 can be picked up for very cheap on ebay, my brother just got one for $20. Hard to beat that for the price.

---

### Post by rockstarrem on 2009-09-05
Hey,

I have a Creative Soundblaster USB 5.1 Surround Sound and it's working fine after using this utility: [http://ubuntuforums.org/showthread.php?t=759147](http://ubuntuforums.org/showthread.php?t=759147)

There's some cracking at the start of the first song you play on a reboot, but after that you're fine. Once you configure it (type paconfig in terminal) just restart your computer and start playing a few songs, the popping will go away.

I hope this helps, it worked for me.

---

### Post by xstackerx on 2009-09-05
Thank you guys alot for your help. I havent had the chance to try it yet but i will when i get home and ill let you know how it goes. I hope your ideas help but something tells me it wont just cuz i heard that if it has x-fi it wont work. And thats what my card is. but when i got it i was using windows. I may have to just try and get a new sound card. (If the wife lets me of course.lol.) But thanks alot all of ya.

---

