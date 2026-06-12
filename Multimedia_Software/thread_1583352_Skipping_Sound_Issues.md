---
title: "Skipping Sound Issues"
date: 2010-09-27
forum: Multimedia Software
---

### Post by Buffalo_Guy on 2010-09-27
p { margin-bottom: 0.08in; }  Greetings:

Recently new to Linux,  I installed Ubuntu on two computers, an Intel based laptop and a AMD based computer.  I started with the LUCID release and eventually installed Maverick on both.  The laptop performs flawlessly in terms of playing MP3 files and CDs


Th desktop, running an Anthlon II processor and the 64 bit flavor of Maverick has on-going problems playing MP3 files or CDs on any player.  The songs invariably, skip, stop or both.  What I have been able to determine is that is I kill the PULSEAUDIO process, the sound is perfect.  I re-start PULSEAUIDO and the problem is back.  I spent the weekend pouring over all the posts on this issue.  I have tried some of the "fixes" to no avail.  Before I try anything drastic I am looking for any ideas on how to proceed.  I plan on using the desktop for some serious audio and video editing and it would be nice if  Ubuntu can control my audio properties to the fullest extent.    I have been working with computers for years and I am not afraid to get under the hood.  However, my Linux experience is limited and I am curious what more experienced users think.

My audio card is noted below and I thank you in advance for any help or suggestion you can offer.
 

 Steve
 

 -multimedia 
                 description: Audio device 
                 product: RV710/730 
                 vendor: ATI Technologies Inc 
                 physical id: 0.1 
                 bus info: pci@0000:01:00.1 
                 version: 00 
                 width: 64 bits 
                 clock: 33MHz 
                 capabilities: pm pciexpress msi bus_master cap_list 
                 configuration: driver=HDA Intel latency=0 
                 resources: irq:44 memory:fdffc000-fdffffff
 .

---

### Post by gordintoronto on 2010-09-27
Maverick is a beta (testing) release of Ubuntu. You should expect it to crash, be incomplete, and have various other problems. It is not intended for production workloads at this point.

---

### Post by Buffalo_Guy on 2010-09-28
Your point about the state of Maverick is well taken but I thought it was worth a shot to see if the sound issues were any better than in Lucid. 

 In any event I followed the advise of several posters and killed Pulseaudio for now.  I installed the Alsamixer package and all is working without a problem.

---

