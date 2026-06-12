---
title: "No System Sounds - However, YouTube, MP3, etc all work."
date: 2008-08-03
forum: Multimedia Software
---

### Post by Roasted on 2008-08-03
I have no system sounds. Last week I installed a PCI sound card, in which I couldn't get it to completely work, so I took it out and returned it. Both my onboard setup + the PCI card I was using Alsa, but the only changes I had to make were under sys-pref-sounds. Under sounds, right now, everything is selected to Alsa along with my Alsa-Mixer as my sound device. 

I have no system sounds. Yet, YouTube, DVDs, MP3s, etc all work. 

I have no idea where things got switched around.

What I've done so far:

I've ran the command, as suggested to me "sudo /etc/init.d/alsa-utils reset", which yielded no fix.

I also did a complete removal of alsa-base in synaptic and reinstalled it.

What else can I do?

---

### Post by piratebill on 2008-08-03
I had the same issue a while back.  I think all I did to fix it was

sudo apt-get install esound.

This was a while ago...before hardy.  I dont know if hardy has that package by default now or not.

---

### Post by Roasted on 2008-08-03
It's already installed.

I was going to remove it and reinstall it, but when I selected remove it said the following packages will be removed.

It included audacity, amarok, audacious, pretty much anything multimedia related. Maybe I should just hit reinstall on that and see what happens.

---

### Post by Roasted on 2008-08-03
oooooooooooo serves me right for assuming!

The esounds package I had installed (that I thought was the one you were talking about) was esound-common. Sure enough, esound was not installed. I installed it... bam... I got my system sounds back.

Thank you!! 

Note for future reference for those who may dig up this thread - I am running Ubuntu Hardy Heron 64 bit with ALSA sound. Not sure if it matters but figured I'd specify while I thought of it.

---

