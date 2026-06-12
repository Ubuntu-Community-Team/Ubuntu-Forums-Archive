---
title: "Changing channels"
date: 2008-12-12
forum: Mythbuntu
---

### Post by PhilWig on 2008-12-12
A really stupid question from a really raw novice, with some subsidiary ones to check my understanding of things.  

How do you change channels when viewing?   No, be serious, stop laughing!

Channel up/down or up/down arrow changes but very slowly (about 3 seconds), but if I repeatedly press the buttons it freezes "Error was encountered while dispaying video".
The manual suggests that Guide - arrow up/down - OK will select a new channel but that enters a recording screen.
On top of that, I cannot configure it to show all of a channel name - I'll typically get ITV1 W  instead of ITV1 Wales or BBC R instead of BBC Radio 3; also since they are in a funny order finding them is terrible.

Mute doesn't work either - MUTE ON or MUTE OFF show on screen, but the sound continues.  I've used alsamixer to boost sound levels but doubt it relevant.

Setup:  
------
UK, DVB-T.

Pentium4, 3GHz, 1GB, VGA screen, normally running XP but with a Hauppauge T500 (PCI but twin USB internally) added and the XP system disk swapped for an old PATA 8GB dangling by the wiring  to try out MythBuntu.
If successful I'll buy 'proper' sitting room hardware. 

Mythbuntu version 8.04 (Myth version 0.21). 

T500 on-board amplifier has been turned on successfully and EPG information is available.
Hauppauge remote unit supplied with the T500 and described as 'snowboard'.  Configured as a PVR-150 (PCI) Direct TV Receiver and the buttons seem to work.  All codes are correctly identified with:
   sudo /etc/init.d/lirc start
   irw
Is that sufficient test to prove it's configured right, or do I have to perform the baffling black magic in this page?
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#IR_Receiver](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#IR_Receiver)

This looks a brilliant project but the learning curve is very steep.
Any help really appreciated.

Phil

---

### Post by SiHa on 2008-12-12
About 3-4 seconds is right for a channel change. When you watch TV in Myth it isn't live - it's buffered to the HDD. This pause is to allow the buffering.

> if I repeatedly press the buttons it freezes "Error was encountered while dispaying video".

I've found that with Live TV you need to press a button once, and let Myth do it's thing before pressing another otherise you get just this sort of error.

> The manual suggests that Guide - arrow up/down - OK will select a new channel but that enters a recording screen.

This is an option in the setup (Setup - TV Settings - Program guide). On the second page there's a checkbox, something like 'Allow select to change channels'.

Apart from that, I don't use Mute. I have my '500 setup as a PVR350, but I guess they both work!

I agree - the learning curve is very steep, particularly if you're also a Linux virgin, but it's worth it.

---

### Post by 4dognight on 2008-12-12
> **SiHa said:**
> About 3-4 seconds is right for a channel change. When you watch TV in Myth it isn't live - it's buffered to the HDD. This pause is to allow the buffering.





My cable STB box DVR changes chanels much faster than mythtv does. It is also buffering. So why is myth slower then? This is one of the biggest beefs the other half has with using Mythtv. WAF :)

---

### Post by SiHa on 2008-12-13
Mine too. Probably because the DVR harwdare & filesystem etc is designed from the bottom up for the application and optimized for the task.
Frinstance, the company I work for have developed an IC that can decode two HD streams simultaneously, and it runs @ 25MHz. (There's a fair chance it's the chip in your box!)

Try doing that with a 386!

You need to try and train the wife out of channel-hopping...

---

### Post by PhilWig on 2008-12-13
Thanks - that check box is just the ticket.
Phil

---

