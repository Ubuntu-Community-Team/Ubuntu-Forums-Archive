---
title: "Noob questions - setting up and need elementary advice"
date: 2009-07-31
forum: Mythbuntu
---

### Post by spaceclown on 2009-07-31
I am search challenged so bare with me if these has been answered. I am a noob to Linux and totally green on mythbuntu. 
 
1. I have a PC that should suffice minus needing a larger drive. The processor exceeds requirnments and more than enough RAM. I also have a ATI Radeon X600 256MB PCI Express. Apparently I need a capture card and have some questions. Is there an OOB card I can get that comes with a remote? I will be using broadcast HD only as of now btw. I noticed some also come with FM Tuners. Is this something that is supported as that would be sweet from the main menu to select radio. 
 
2. I want to put in a blue ray player. Is this supported or only DVD's?
 
Basically I need ease of installation. I would like to purchase hardware that just works without tweaking to much on an OS I don't know enough about. If you could supply a link to an actual store that sells it that would be helpful. 
 
I appreciate your help and apologize for the novice questions.

---

### Post by klc5555 on 2009-07-31
> **spaceclown said:**
> I am search challenged so bare with me if these has been answered. I am a noob to Linux and totally green on mythbuntu. 
 
1. I have a PC that should suffice minus needing a larger drive. The processor exceeds requirnments and more than enough RAM. I also have a ATI Radeon X600 256MB PCI Express. Apparently I need a capture card and have some questions. Is there an OOB card I can get that comes with a remote? I will be using broadcast HD only as of now btw. I noticed some also come with FM Tuners. Is this something that is supported as that would be sweet from the main menu to select radio. 
 
2. I want to put in a blue ray player. Is this supported or only DVD's?
 
Basically I need ease of installation. I would like to purchase hardware that just works without tweaking to much on an OS I don't know enough about. If you could supply a link to an actual store that sells it that would be helpful. 
 
I appreciate your help and apologize for the novice questions.

I'll leave it to others to answer the remaining questions, but I will say that with the current version of Mythbuntu, you're likely going to run squarely into a bug that affects ATI Radeon graphics. As described under "Known Issues" here:

[http://www.mythbuntu.org/9.04/Release_notes](http://www.mythbuntu.org/9.04/Release_notes)

Tuner cards that are known to work in mythtv are summarized here: [http://www.mythtv.org/wiki/Tuner_Card#Cards_that_work](http://www.mythtv.org/wiki/Tuner_Card#Cards_that_work)

---

### Post by spaceclown on 2009-07-31
> **klc5555 said:**
> I'll leave it to others to answer the remaining questions, but I will say that with the current version of Mythbuntu, you're likely going to run squarely into a bug that affects ATI Radeon graphics. As described under "Known Issues" here:
 
[http://www.mythbuntu.org/9.04/Release_notes](http://www.mythbuntu.org/9.04/Release_notes)
 
Tuner cards that are known to work in mythtv are summarized here: [http://www.mythtv.org/wiki/Tuner_Card#Cards_that_work](http://www.mythtv.org/wiki/Tuner_Card#Cards_that_work)
 
thanks for the info. I do have the old card - Silicon Image - Orion Add2 Dual Pad x16 card I could use also.
 
As for the tuner cards I assume being I am only wanting broadcast HD that "[DVB-T]("http://ubuntuforums.org/wiki/DVB-T") cards (Terrestrial viewing)" is the correct assumption.

---

### Post by klc5555 on 2009-07-31
> **spaceclown said:**
> thanks for the info. I do have the old card - Silicon Image - Orion Add2 Dual Pad x16 card I could use also.
 
As for the tuner cards I assume being I am only wanting broadcast HD that "[DVB-T]("http://ubuntuforums.org/wiki/DVB-T") cards (Terrestrial viewing)" is the correct assumption.

DVB-T (VSB-8) is over-the-air digital. Unencrypted digital cable (QAM-256 or QAM-64) uses dvb-c. Many cards will be able to do both.

For graphics, you're strongly advised to invest in at least a modestly priced NVidia GeForce card. 6xxx, 7xxx, 8xxx, or 9xxx series. Much better driver support, and with the NVidia proprietary Linux drivers, you'll be able to do HD-quality playback on it. As basically described here: [http://www.mythtv.org/wiki/NVidia_Cards](http://www.mythtv.org/wiki/NVidia_Cards)

---

