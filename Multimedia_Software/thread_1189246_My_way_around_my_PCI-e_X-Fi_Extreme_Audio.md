---
title: "My way around my PCI-e X-Fi Extreme Audio"
date: 2009-06-16
forum: Multimedia Software
---

### Post by AoSteve on 2009-06-16
Alright, I didn't get many responses to my problem, either noone knows or it's just never been fixed before.  I've read where the X-Fi Extreme Audio PCI will work with the creative drivers out now, but never saw one post about the PCI-e version.   So..  I have fought with these drivers for what seems to be an eternity, in silence...

Well, try and try again.  I installed the drivers, both automatically and manually through the terminal.  Even upgraded ALSA and OSS manually..  Nothing..   Not even a hint of sound coming from the speakers.   I've officially tried everything for this card to work.  I will be replacing it soon enough with something a little better..  *cough cough* Xonar DX...    

I'm not an audiophile or will I ever be one..   But when I'm at my computer doing my schoolwork, messing with a conky configuration, or just browsing...  I like my music to be running in the background.   Yet, nothing I did to my X-Fi Extreme Audio would allow me to do this.

So, I had an old Sound Blaster Live! sitting in my desktop that's attached to my TV.  Well, I ripped it out, installed it and booted to Linux.    WHAT?!?!  DRUM SOUNDS?!?!?  SWEET!   

So it works, no modifications needed what-so-ever.  Perfectly, and to be honest, it sounds better on this machine then the X-Fi does in windows, actually a LOT better.   So, here's my plan.   Since I have a 5.1 system here, I'm going to run the setup with three splitters so I can have them attached to both cards.   I don't use Vista much, other then for school, but when I do, WMP11 is on.   I'll have sound there, and in Ubuntu.  

I can't stress how happy I am right now.   However, there's something I must emplore to you guys who may try this with your PCI-e X-Fi Extreme Audio's...  

When I boot into Vista, all seems well until I try to play a file or whatever.  Linux gives you direct control over the output devices, unlike Vista.   Vista always tries to use the SB Live! first, and this causes a major lag on opening files.  Plus, it seems choppy with the sound.   So, what I did, I kept switching the PCI slots of the SBLive until I got an IRQ that wasn't paired with anything else important (my second lan controller and my serial port).   Now, it doesn't lag, but windows bugs me every time I boot about new hardware.    You must run through the setup, allow it to tell you there's no drivers for the device.  Once you can get out of the wizard, do so.   Hit up the Device Manager and disable the "unknown" multimedia device and the "unknown" Input device" and you're ready to roll.

Now, windows doesn't bug me on bootup, and I have no lag or skipping effects by the bad IRQ's.   Just so happened, the Live! had to be in my last PCI port on my mobo to get it to match the IRQ's that I liked.  :)

---

