---
title: "HVR4000 TVcard - DVB-S and DVB-T suddenly not recognised - only analogue"
date: 2019-11-10
forum: Multimedia Software
---

### Post by plainfaceboy on 2019-11-10
Hi - I've been running 16.04 with Mythtv 0.29 for some years all fine. Video card is the quad Hauppauge HVR4000.
DVB-S, DVB-S2 and DVB-T all good.
Never tried the analogue but recently wanted to transfer some old VHS so tried to set it up.
Couldn't get an image in via the s-video (but that might be related to my VHS only outputting composite) other than black and white, and sound was distorted, but in my various attempts, including using TV Time, *suddenly* TVtime went from seeing inputs of;
TV, Composite and S-Video....to seeing inputs of; 
Composite 1, 2, 3 and 4.
Now composite 3 worked fine with the image which was full colour, but there was now no sound.
Also, when I went back to Mythtv I thought I'd re-add my cards to clean it up (as I'd previously added an analog V4L card to try and get the VHS), but the DVB-S and DVB-T were not recognised.

I thought I'd take the opportunity to try a fresh install of 18.04 and mythtv 30 but the same thing is happening - no DVB-S or DVB-T recognised in mythtv.
I'm not at computer at moment but generally;
cx88 shows up in lspci (a single line)
and dmesg has the line about no PCI subset so card can't be detected.
I add mprobe cx88 card=68. (68 is for Hauppauge HVR4000)
Do I need to do something for DVB-S and T?
I've tried the card in a different PCI slot. I'm confused as had assumed a fresh install of 18.04 would have picked up the card, as every other time it has done.
Is it a kernel issue?
Is it a card issue?
Can anyone help?

---

