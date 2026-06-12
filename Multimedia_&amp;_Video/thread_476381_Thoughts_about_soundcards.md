---
title: "Thoughts about soundcards?"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by Silent Warrior on 2007-06-17
I'm one of those poor souls who dual-boot Ubuntu/XP with an X-Fi XtremeMusic as a primary soundcard. I'm now getting... annoyed by constantly moving the cables from there to the onboard sound-connectors to get my well-deserved sound in Ubuntu. Creative are apparently supposed to get their act together and have drivers ready some time in July, but just in case, I'm looking at forming a contingency-plan. Something along the lines of: Oi, get a new soundcard, foo'!

First things first, I noticed that other [topic]("http://ubuntuforums.org/showthread.php?t=463921&highlight=X-Fi+XtremeMusic") where there was suggested that the XtremeMusic CAN be used in Ubuntu. I'll try the suggestions listed, but since the Device Manager claims I have an X-Fi Platinum (yes please!), I'm not all that optimistic.

So, what somewhat snazzy soundcards work in Ubuntu? It'll see a fair degree of usage in WinXP too, but I have a feeling that won't be a problem. I'm mainly looking for something with optical In (MD transfer, PS2 sound). As always, better sound-quality is a plus. Though my speakers (5.1) are probably holding me back in that area... What is on the Live!Drive called S/PDIF wouldn't hurt, either - that way I can hook up my other system to my speakers as well. (Different connections on the speaker rig.) Whee! :cool:
Main usage will be listening to music and playing games.

I'm mostly interested in your experience of... whatever card. Both XP and Linux.

So far, I have looked at...
[Auzentech]("http://www.auzentech.com") - VERY appealing, but doesn't seem to have Linux-support for all their gear yet. So far, they've mostly worked with C-Media-chips (a few are supported according to ALSA, but not the really cool stuff), but now they have something coming based on an X-Fi-chip. That card, however, might be more than I'll find use for.

[Turtle Beach]("http://www.turtlebeach.com") Montego DDL - Apparently without Linux-drivers today, but they seem to look kindlier on the idea than Creative does.

[AudioTrak]("http://www.audiotrak.net") - That Prodigy 7.1 seems to be what I'm looking for among AudioTrak's products. It seems to lack optical I/O, but its sibling, the Prodigy 192, has it but seems to be aimed at the audio-pro. Which isn't me. Drat.

RME-audio also has interesting gear, but they seem to be for pros as well. SERIOUS pros. Really funky connections on the back... AND there are expansion-boards. Yikes in a box and then some...

[M-Audio]("http://www.m-audio.com") - There are some neat things to look at there. They manage to make themselves look like they're for the MIDI/composer type of clientèle, but what the hell. If it's good gear, it's good gear.

Now, I said an eventual purchase would have to wait until at least July, so "things" may happen on the soundcard-front. There are bound to be more cards to choose from, as well. ASOUND, a Chinese bunch, uses C-Media chips and name their cards after the chip. Might be interesting, then again, maybe not. M-audio exist, too, but seem to be geared at professionals, MIDI-users in particular.

Well, over to you, I suppose.

---

### Post by dabl on 2007-06-17
I'm very pleased with the Intel HDA system that is integrated on my Intel D975XBX motherboard.  I've been using it for recording from old 78 and 33.3 rpm records, and it does a great job using ALSA.  The specs aren't as impressive as a truly professional sound card, but they're not too shabby either.  Here they are:  [http://www.intel.com/design/chipsets/hdaudio.htm](http://www.intel.com/design/chipsets/hdaudio.htm)

So, my motherboard looks expensive until you factor in the cost of a "cheaper" motherboard, plus a good sound card, and then it seems like a pretty decent deal.  :D

---

### Post by Silent Warrior on 2007-06-18
Well, I'm on an AMD AM2 platform myself, (ASUS M2N-E, integrated SoundMax AD1988 ) but I suppose it isn't to be ignored altogether. :) I'd be quite amazed if it doesn't whip the tail-feathers off my present on-board soundchip...

---

### Post by Silent Warrior on 2007-06-20
Hm... Doesn't anyone at all have something to say about this? Not even a groovy onomatopoetic word? :)

*Ker-BUMP*

---

### Post by oyvey on 2007-07-23
I'm in the same fix (Creative X-treme Music for Windows XP + Intel HDA for Linux Ubuntu) and can't help, indeed I have an additional problem : when the integrated audio is BIOS-enabled, Windows XP doesn't properly handle the front speakers until I use the Device Manager to  deactivate  the Intel HDA (I've read somewhere it's a bug in XP but can't find the reference anymore). Or rather re-activate and re-deactivate it, since the Device Manager doggedly considers it is deactivated. From what I hear I believe it is activated at boot time, then wrongly deactivated. How do you handle that, I mean the coexistence of two sound cards in XP ?

---

### Post by Silent Warrior on 2007-07-24
I wouldn't say my way is THE way, and I haven't noticed any bugs in speaker-management.
As for my present set-up, I have the on-board sound disabled through Device Manager, and, as I need it for Ubuntu, enabled in BIOS (and it's the only detected device for ALSA). I get sound in both OSes, and it works for me. I wouldn't know if the sound-quality is all that, but sound AT ALL is better than no hi-fi-sound.

Well, as far as XP is concerned, I probably answered that already. I have no problem of any sort, no error-message, no peculiar crash... But is it ever annoying to crawl down on the floor and shove those cables around... I'm not getting any younger, Creative!

---

### Post by Yellow Pasque on 2007-07-24
I'd look into the M-Audio Delta/Audiophile 2496. At least M-Audio has linux drivers that are updated with some degree of frequency (opensound.com) .

I'm using an M-Audio Revo 5.1 and it works great for playback. Input appears to be supported as well, though I don't have personal experience with that.

---

### Post by Silent Warrior on 2007-07-24
Hm, no optical input, but maybe that can be arranged with some snazzy speakers. (Or maybe I can look at a whole new stereo-rig - the one I have is about as old as I am...) But it does indeed look nice.
Heeey, there's that CO2-thing! Coolness incarnate! A bit costly, but it looks like something I can use to hook up my PS2 to and not have any problems. Innnnnteresting... M-Audio r teh nic3.

---

