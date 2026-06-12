---
title: "onboard sound issue: ECS G31T-M board"
date: 2009-04-04
forum: Multimedia Software
---

### Post by beermotor on 2009-04-04
Hi all - I've tried everything that I found on the web and the forums, but nothing seems to address my issue.  My board, the ECS G31T-M, has onboard audio that is, supposedly, 5.1 (I think it's a Realtek AC662, but appears to respond to snd-hda-intel module?).  The rear jacks, however, default to line-in (top), line-out (middle), and mic (bottom).  Unfortunately, there is no bios control for this, it's software controlled.  In WindozeXP, there is a driver program that will allow you to remap the top line-in jack to a rear-line-out ... which is what I want, as I have a 4.1 setup.  But I'll be danged if I can find any way to do this in Ubuntu.  Sound plays fine and great through the two speakers and the sub, but nothing comes through the rear speakers.  I've altered /etc/pulseaudio/daemon.conf default-channels to 6, still doesn't work.  In looking at both alsamixer and the gnome alsamixer, I am pretty sure that linux/Ubuntu is just not reading that top jack as a line-out.

Anyone know of a way to fix this?

---

