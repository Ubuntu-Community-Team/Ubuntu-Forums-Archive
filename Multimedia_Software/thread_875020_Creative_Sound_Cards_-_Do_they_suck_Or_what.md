---
title: "Creative Sound Cards - Do they suck? Or what?"
date: 2008-07-30
forum: Multimedia Software
---

### Post by Roasted on 2008-07-30
Since I am on the desperate hunt for a fully supported PCI sound card in Ubuntu and have yet to find one that's worth my time to look at, I am considering all options. I keep hearing people shreeking that they can't get their Creative card to work. Others are like omgosh Creative is so easy they have Linux drivers on their web site!

So, what's the story? Should I consider a Creative SoundBlaster card or something? Something that they have a driver for on their site? Or pray that I can get my SIIG SoundWave 7.1 card to work before I consider returning it?

---

### Post by Trollslayer on 2008-07-31
My experience is thaat Creative don't supply infromation for the writing of linux drivers to they have to be reverse engineered.
My pesonal choice is the Asus Xonar D2 now that it has full support in the latest vewrsion of ALSA (1.0.17).
Gamers note - wave tables with this are handled by the CPU. Creative handle wave tables internally which is better but DTS etc. support is poor.

---

### Post by jukingeo on 2008-09-23
> **Roasted said:**
> Since I am on the desperate hunt for a fully supported PCI sound card in Ubuntu and have yet to find one that's worth my time to look at, I am considering all options. I keep hearing people shreeking that they can't get their Creative card to work. Others are like omgosh Creative is so easy they have Linux drivers on their web site!

So, what's the story? Should I consider a Creative SoundBlaster card or something? Something that they have a driver for on their site? Or pray that I can get my SIIG SoundWave 7.1 card to work before I consider returning it?


That all depends on what you want to do.  If you "just want sound", then the Soundblaster Live or Audigy should do the trick and in many cases the card is automatically detected.

However, if you want to use your machine for higher end audio work, like say for a DAW application, then Creative does suck.  Reason being is that you are set at one sample frequency, which is 48k.  You can't go higher, you can't go lower.

The Sound Blaster X-Fi, while not fully supported WILL work outside of this restriction, but it is a fairly lengthy procedure to get going (see the link in my sig below), and will require a slightly above average knowledge of computers and Linux in general.

I found the X-Fi limiting in that you can only get it to work in certain versions of Ubuntu (Gutsy/Hardy), and OpenSUSE.   So, I have other distributions as well in which the X-Fi will not work at all.

Supposedly people are having good results with the M-Audio Delta Line of audio devices.   They are usually automatically recognized as well, and they are Linux supported via M-Audio (unlike Creative M-Audio DOES provide a Linux driver).

So, sadly, there really isn't much that is supported right now in Linux.

I also have an Echo Mona sound device that I bought because the ALSA website says it is supported, however, the card isn't automatically recognized by the system, and I am working on two months to get the device to work.   So I wouldn't always go by what the ALSA site says either.

Probably I am going to sell off my Echo Mona and try out an M-Audio card.

So in conclusion, for regular system/game sound, you are good to go with Audigy and SB Live.  For a Daw based system M-Audio seems to be the only [I][U]affordable[I][U] route right now.  RME Hammerfall cards are also supported by Linux, but they are EXTREMELY expensive.  But that is probably your best option for a professional/commercial Linux based DAW sound device.

Hope that helps!

---

### Post by markbuntu on 2008-09-23
My SIIG Soundwave 7.1 PCI card worked out of the box. Plugged it in and have had zero problems. I did not have to screw around with editing any files, recompiling my kernel, finding patches or drivers etc. 

I only had to change three settings, the default in the Pulse Audio Volume Control, a right click, and the device and preference in the Volume Control, a few more clicks. I also had to move a few cables around from my on-board sound to the new card but we can't count that.

---

### Post by Roasted on 2008-09-23
Mark - you're running 32 bit, aren't you? I forgot I was running 64 bit ubuntu when I had the SIIG card. I returned it without even thinking about it. After I had ordered my Montego, I installed 32 bit. Worked perfectly... and I believe the Montego and SIIG have the same audio chipset.

---

### Post by markbuntu on 2008-09-24
I am running 32 and 64 bit and hopefully soon Intrepid. I believe you may be correct about the chipset, it is C-Media 8768. C-Media also has other chipsets in the 87xx series 8738 and 8758 but I think they are just 2.1 and 5.1 surround versions.

I can record no problem and the midi works with hydrogen and rosegarden. the 3D switch also seems to work. I see no difference with the card on 32 or 64 bit. Maybe you got a bad card.

---

