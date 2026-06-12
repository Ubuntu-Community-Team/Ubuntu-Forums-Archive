---
title: "KWORLD PlusTV HD PCI 120 on Ubuntu 8.10"
date: 2008-11-27
forum: Mythbuntu
---

### Post by jeff45 on 2008-11-27
Has anyone else had success with this card.  I've done everything in the tutorial on the LinuxTV site - upgrade kernel, upgrade firmware, etc.  (I'm still a noob here)   After following the tutorial, I can select the card in mythtv backend setup. However, I don't have a selectable intput - maybe this is because you can only use either the ntsc tuner or the Atsc one but not both.  I've run the channel scan and it appears to see them.  My fronted has these digital channels on the program guide, but if try to set them to record, the frontend hangs. 

I'm using a Poweredge 2450 w/ 2 PIII's@1Gzh 2U as my primary backend.  I really don't think its a hardware issue cause my PVR150 works fine.

I also read a post somewhere showed "ATSC" as an option for the "Brocast type" under general settings on mythtv-backend setup.  I don't seem to have this option.  Can I not have ATSC and NTSC on the same backend?

---

### Post by jeff45 on 2008-12-04
I finally got this working.  I can confirm this card works.

---

### Post by beubank2 on 2009-01-11
Jeff45

I too have the Kworld Plus TV PCI 120 card, and would really appreciate some help setting it up.  Could you please tell me how you did it?

---

### Post by swalke66 on 2009-02-23
I have one of these cards as well. 

I installed mythbuntu 8.10 and both the analog and DVB parts of the card are automatically detected.  

I can get analog video in no problem (although no audio!) but haven't had luck with DVB yet.  I've seen indications of others getting this card to work ok,  Can anyone help with this?

---

### Post by swalke66 on 2009-03-05
I currently have this card working with analog video.  My cable company (Rogers) apparently uses QAM-256 modulation, which this card doesn't appear to support so guess I am SOL!

I still have not been able to get audio functioning in MythTV however.

- There is an audio out on the card which works but the audio is horrible quality and full of pops and clicks.
- I have selected /dev/dsp as my audio device (this gets me audio when playing music)
- the audio through device is 'default'
- however still I don't have any audio when 'watching tv'

Can anyone help with this card?

---

### Post by NinjaNumberNine on 2009-07-20
This is the Step-by-Step installation site for your card.
Click [[COLOR=Red]HERE[/COLOR]]("http://www.mythtv.org/wiki/Kworld_ATSC_120")


-but then, I couldn't even get **them** to work! :mrgreen:

---

### Post by vertago1 on 2011-01-26
> **NinjaNumberNine said:**
> This is the Step-by-Step installation site for your card.
Click [[COLOR=Red]HERE[/COLOR]]("http://www.mythtv.org/wiki/Kworld_ATSC_120")


-but then, I couldn't even get **them** to work! :mrgreen:

that link has since been killed, [http://linuxtv.org/wiki/index.php/KWorld_ATSC_120]("http://linuxtv.org/wiki/index.php/KWorld_ATSC_120")
Has instructions. I am trying to get the channel scan to find the channels.

---

