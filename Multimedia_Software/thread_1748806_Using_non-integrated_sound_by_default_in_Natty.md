---
title: "Using non-integrated sound by default in Natty"
date: 2011-05-03
forum: Multimedia Software
---

### Post by jalefkowit on 2011-05-03
Hey all...

So I did the update to Natty and it went pretty smoothly, with one exception.  My rig has two sound cards in it: the integrated motherboard sound card (Intel HDA audio) that I don't use, and a Sound Blaster Audigy (the original Audigy 1) that I do use.

This setup has worked fine in Ubuntu for as long as I can remember, but after the upgrade to Natty it appears that GNOME no longer knows that the Audigy is the card that's in use.  It insists on routing things like volume changes via gnome-volume-control to the motherboard.  I can confirm this by watching the volume levels for each card in alsamixer while modifying them in gnome-volume-control; the levels move appropriately on the integrated card, and stay stuck on the Audigy.

What makes this bizarre is that it's not that the Audigy isn't recognized -- it's shown in the "Hardware" tab of Sound Preferences, and the system plays back audio just fine through the speakers connected to the Audigy. It's just that I can't change the volume on the sound through the panel applet anymore.  Normally I would fix something like this by using the Hardware tab to switch from the one card to the other, but in this case when I make that change it doesn't stick -- if I close the Sound Preferences and then open it again, it's right back to being set to the integrated audio.

Maybe this is a PulseAudio issue with older Audigy cards?  I have no idea.

I can change the volume with my speakers' volume knob and my keyboard's media keys, I suppose, but I'm so used to be able to change it via gnome-volume-control that not being able to feels bizarre.  Has anyone else out there with add-on sound cards installed alongside motherboard audio experienced this?  Any ideas on how to get it fixed?

Thanks!

---

### Post by wolfen69 on 2011-05-04
Did you turn off the integrated sound in the BIOS?

---

### Post by jalefkowit on 2011-05-04
That did it, with one caveat: when I booted into Natty after disabling integrated sound in the BIOS, I had no audio at all.  But Sound Properties now showed only the Audigy card in the Hardware tab, and after I selected that, sound returned and all the GNOME sound bits and bobs worked properly, including volume control.

I'm not sure what changed in Natty that required this, since I've been using this same rig without the BIOS settings change with Ubuntu for years with no problems, but at least everything works ok now.

So, thanks! :KS

---

