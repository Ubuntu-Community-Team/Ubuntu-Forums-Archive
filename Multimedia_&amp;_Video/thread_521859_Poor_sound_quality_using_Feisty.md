---
title: "Poor sound quality using Feisty"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by craigiedan on 2007-08-09
While playing mp3's using Rhythmbox, XMMS, or Audacious, I hear crackling and popping when I move the mouse or open and use other programs such as firefox. Also, when playing flash videos online, the sound is almost inaudible due to the crackling.

I'm using a SB Live! with all the necessary codecs and drivers installed. I've played with ALSAMIXER and reinstalling the ALSA package along with numerous other fixes to no avail. Along with that, I've yet to get sound from my rear speakers. 

Help!!!

---

### Post by jeremy1138 on 2007-08-09
I have that same problem...  I'm using VLC Media Player...  I wonder if there is some other driver we're supposed to have installed for the sound card?

---

### Post by craigiedan on 2007-08-10
I thought about it, but when I look at the ALSA page for supported drivers, I have the necessary driver installed for my soundcard. (emu10k1)

At this point I'm almost considering purchasing a new sound card; disappointing, but perhaps necessary.

---

### Post by jeremy1138 on 2007-08-10
I wish I had the option to just buy a new sound card...  I'm stuck with my laptop...

---

### Post by sabthagiri on 2007-08-15
Hi All,
Found the following article on the official Ubuntu Help Community site:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

The symptoms listed here look similar to what you guys are facing. I tried it out and it worked for me. Think we need to recompile ALSA drivers.

Cheers!

---

### Post by craigiedan on 2007-08-20
Yeah, I already rebuilt my ALSA package and made sure it was updated, but to no avail.  I'm running Feisty on a laptop with a new sound card, so I'm guessing that's the case. If anyone has an idea about surround sound, that would be great. I've tried a few fixes, but nothing works...

---

