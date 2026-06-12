---
title: "Updated Info Please"
date: 2009-07-31
forum: Multimedia Software
---

### Post by usmcstitch on 2009-07-31
Hi all.  I've been doing alot of research lately.  ALOT.  I'm trying to build me up a mythbuntu box(s) to service my home and need some (updated) advice.  May be a long post.  Sorry in advance.

In short, I'm looking for a good TV tuner for my myth server I'm trying to build.  All the information i'm reading seems to be from last year (or later!). I have found very few posts from this year, what with the new kernel updates, USA digital TV switch, new cards etc...  
**Here's the setup:**
**1.** House wired C6 /GBE switchs & NICS
**2.** I have a Dell 755 Intel Core2 Quad 6600, 4GB RAM, either a ATI HD2400XT or Nvidia 7900GS (which is better for HD viewing?).  Everything is running Ubuntu 9.04 fine and dandy w/ kernel 2.6.28-14 (though I might upgrade to 2.6.30)
**3.** I have Comcast Digital Starter Package w/ HD and a SA4250HDC STB w/ Firewire, Composite, HDMI.  This is in the Living Room.  Digital Starter has stuff like HistoryHD and DiscoveryHD, VS HD, Comedy Central HD, Cartoon HD etc.  No HBO or s**t like that.  
**4.** I have a LCD Tv in the bedroom w/ a built in QAM tuner, and I get the Clear QAM Channels like NBCHD and the digital crap.  The problem here (which relates directly to my questions below) is that the channels are wonky.  For instance, I get 5 NBCs.  Analouge NBC(420) = 3 & 12.  NBC Digital = 56-3(420) & 74-3(420) and , NBCHD(1080) = 103-2.  The numbers may not be exact, but you get the gist.  
**5.** I want to use the Mythbuntu to stream TV (and music/pics etc) to 2 or 3 rooms in the house, each using a myth front end on a PC.  I'll put a PC in the bedroom connected to the LCD, and the kid has a 22" Monitor for his computer and TV (eventually, if the TV thing goes well) 

Again, I've done ALOT of reading and research, but its all outdated, pre-digital switch over, so I'm looking for some "today" answers.

**Question time:**
**1.**  As of July 31, 2009.  What is a good tuner that can service at least 2 rooms and works flawlessly in Mythbuntu/Mythtv.  I prefer to use the PCIe x1 slot, as I have a SATA Raid card on my PCI Bus supporting 3 drives in RAID10.  
   - I've been teetering on the Hauppauge WinTV-HVR-2250 Dual TV Tuner, Hauppage 1800, or the ever popular HDHomerun.  How is the support on the 1800 and 2250 now? ***EDIT BELOW***
   - I know the HDHomerun is the tuner of choice, but I see 2 problems. First, it doesn't do Analogue.  Second, I would need to split my cable signal for the 2 feeds.  Again.  wouldn't this cause signal degregation? 
   - I'm not partial to any particular brand.  I just need a tuner that works with minimal effort in Myth, good picture quality, and preferably PCIe1.
   - Antenna/OTA is not an option.  There is no good reception where I live.  
**2.**   Why do I even need an analogue tuner?  I thought everything is digital now, why am i still getting 1-79 analogue on Comcast?  
**3.**  Will I still get the wonky channel numbering in using the digital and/or ClearQAM?  which leads me to:
**4.**  How does Schedules Direct handle the crazy numbering?  I'm assuming that my 1-79 channels will work (except for the HDHomerun right?) as normal, but will SchDir display 103-2 NBCHD, 78-18 HGTV etc. as such in the Guide?  Will they display at all?
**5.**  Regarding the SA4250HDC.  What are my options w/ this?  I'd like to have all my HD channels that I have available via the STB, but inside Myth.  Recording HD would be a bonus, and streaming to other Myth Frontends would be the money shot.  the only 2 ways i see this working is via Firewire and the Hauppage HDPVR.  From what i've read, the HDPVR isn't quite ready yet.  Problems w/ the IR blaster?  Is it a pain to setup in Myth?  Firewire is iffy from what I understand.  I'm not sure if the Comcast controller would work with either of them, and I don't know if I can stream to other Frontends through the house.  

I'll probably have more questions, but this is a good start.  I've tried to do my homework, but i'm suffering from information overload and outdated info.  

Thanks for any info you can provide me.  I really want to get this project launched.

-Stitch

**EDIT**:  It seems that the Hauppage WinTV2250 is "sortof" working now, thanks to LowSky.  However, I understand analogue is not working.  This harkens back to my original questions: does Schedules direct see or make sense the fracked up channels given out by QAM, so I won't need analogue.  And do I even need analogue.  As long as my wife can get her mexican soap operas and me my History Channel, its all good.

---

