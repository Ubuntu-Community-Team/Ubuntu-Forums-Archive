---
title: "Intel HDA 82801G (ICH7 Family) - Volume control jumps during adjustment"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by chriswyatt on 2008-01-03
I have a HP Pavilion DV2058ea laptop with onboard sound:  Intel 82801G (ICH7 Family) High Definition Audio Controller. This has a microphone, headphone 1 jack and a headphone 2/SPDIF jack, seems to be set up as 2 headphone jacks because they both output the same thing.  Switching from laptop speakers to headphones is done by the drivers, this works fine.  When I try to adjust PCM using the GNOME volume control applet the slider hops all over the place and PCM also mutes and unmutes itself which is really annoying.  Also, when controlling inside the applet the left and right channels become unlocked and end up being different to each other which makes things even more annoying.  Weirdly, I didn't have this problem before, I recently did a fresh install of Ubuntu hoping it would fix the problem but it's still there?  Oh, and the problem seems to only be on PCM, the other controls are fine.

I have another problem with the mapping of each control which makes me wonder if the wrong module is installed for my laptop perhaps?  PCM is the master control, it affects both the laptop speaker and sound through the headphone socket but mute only works through the headphone socket.  Both PCM-2 and Speakers control sound through my laptop speakers, mute works on both of these, Headphone doesn't appear to do anything.

Has anyone with this setup managed to get things working a bit more smoothly?  I'm managing OK with it now but I would be grateful for any suggestions.

---

### Post by Tomone on 2008-01-06
I have the same kind of problem, but it's only for the PCM setting for my Powerwave USB Audio. (The rest of the volume settings work fine.) When I use the keyboard shortcuts to adjust the sound, it bounces up and down, but never too much above zero. Then when I try to adjust the volume sliders in the gui, the two channels unlock and the left channel jumps to zero. If I try to move the left channel up, it bounces up and down from the position of the pointer to zero. Also, I didn't have this problem in Feisty.

---

