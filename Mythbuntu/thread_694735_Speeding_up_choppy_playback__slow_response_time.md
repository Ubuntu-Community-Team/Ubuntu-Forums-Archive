---
title: "Speeding up choppy playback / slow response time"
date: 2008-02-12
forum: Mythbuntu
---

### Post by JRGould on 2008-02-12
So, I finally got my Mythbuntu box running  to the point that I am enjoying the crap out of it, the only problem is that the video playback is choppy. Sometimes it's just a slightly reduced frame rate, but sometimes it looks like it's running at 8fps tops. Also the UI can be a bit  slow to respond and anything prompting an OSD (such as changing volume) will drop the fps, as will using MythWeb from my laptop while watching TV.

So, are there any good tips on how to speed this thing up? I'll consider software and hardware solutions.  I'd even considering buying a new box from dell.com/open , but I don't want to spend much more than $400 in total. 

I'm running an HP Vectra system with
1.6GHZ processor
768MB SDRAM
ATI RADEON 7500 (pci)
Haup. PVR-150
and 2 40 gig HDs (system is running on sda1 and storing video on sda2)

The dellbuntu machines aren't much better equipped than that, which leads me to believe that I could beef this machine up for a few hundred dollars and have something that will work great. Or that my issues might not even be rooted in my hardware, but poor configuration on my part.

---

### Post by theacoustician on 2008-02-12
First off, what kind of videos are you watching?  Codec type, resolution, etc.  will help dictate hardware requirements.

> 
The dellbuntu machines aren't much better equipped than that, which leads me to believe that I could beef this machine up for a few hundred dollars and have something that will work great. Or that my issues might not even be rooted in my hardware, but poor configuration on my part.
Um, you can get a C2D with a gig of DDR2 for under $400 at Dell with Ubuntu installed.  That machine would absolutely smoke your current box.  I think the problem here is you're not taking into account bus speed increases, the usefulness of dual cores, north and south bridge improvements, etc.  Your current machine is in no way, shape, or form comparable to currently available systems.

This isn't to say what you have is no good.  It may be perfectly acceptable given your application, but you'd really have to answer opening question in order to get a better read on what you need to do to solve the problem.

---

### Post by JRGould on 2008-02-12
I'm watching SD video encoded however the pvr-150 is spitting it out;  looks like mpeg-2 TS at 480x480, I don't really understand the encoder settings very well so I haven't fiddled much with them since setting the thing up


> I think the problem here is you're not taking into account bus speed increases, the usefulness of dual cores, north and south bridge improvements, etc.

That makes sense, now I'm thinking a new Dell would be a pretty good investment.

---

### Post by newlinux on 2008-02-12
For you OSD problems, make sure you are using minimal OSD effects (somewhere in the setup menu) and different OSD will perform differently. What is your CPU utilization when playing videos?

And yeah, for $400, you could build a good HTPC system. I think $400 towards a new machine makes mroe sense than hundreds of dollars towards this system. That said, this system should be plenty strong enough to play everything but HD (I assume your current system is 1.6Ghz, not 1.6Mhz.

Also, ATI GPUs are sometimes an issue in Linux... and maybe your hard drive performance isn't very good. Lots of variables...

I have found for my PVR-150 the best quality for my machines comes by setting the resolution to 720x480 and the codec to DVD-Special 2

---

### Post by JRGould on 2008-02-12
> I assume your current system is 1.6Ghz, not 1.6Mhz. Hah, nope I'm actually running Mythbuntu on a calculator :) amended.

> I have found for my PVR-150 the best quality for my machines comes by setting the resolution to 720x480 and the codec to DVD-Special 2 thanks, I'm going to try those settings out, and probably buy a new computer, put this to work as a SA frontend

---

