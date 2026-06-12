---
title: "[SOLVED] No Sound, using SPDIF, NVidia ALC882"
date: 2008-09-11
forum: Multimedia Software
---

### Post by elwyn on 2008-09-11
Hey
I have recently installed Ubuntu 8.04 x64, everything works great except my sound.
I play any sound files/websites/flash/youtube etc, and get nothing.

aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [VOIP USB Phone           ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I assume I want card 0 device 1?

I have checked that the right card is selected, and of my options (NVidia, default), I have NVidia selected.

The next thing I have tried is typing *alsamixer* in the terminal.
Everything looks fine here however, nothing is muted (except mics/front line ins etc), and IEC958 is green (unmuted)
From searching, IEC958 appears to be the SPDIF setting?

Aside from what I have done, I am out of ideas. I have read [this thread](http://ubuntuforums.org/showthread.php?t=205449) without much luck, and am stumped.

The only other thing I can add is when I enabled IEC958 from the volume controls, it started a slight crackling in my speakers when they are loud, but still no sound.
Oh also the sound works fine in Windows XP.

Any help is appreciated!

Elwyn

---

### Post by at0mic on 2008-09-11
Hi, I have the ALC883. see my thread here:

[http://ubuntuforums.org/showthread.php?t=912566](http://ubuntuforums.org/showthread.php?t=912566)

Id suggest totem for testing.

---

### Post by elwyn on 2008-09-11
> **at0mic said:**
> Hi, I have the ALC883. see my thread here:

[http://ubuntuforums.org/showthread.php?t=912566](http://ubuntuforums.org/showthread.php?t=912566)

Id suggest totem for testing.

Heya-
I did actually read your post, that's how I first learned to turn on ICE958, thanks
And when in alsamixer ICE958 is not muted, so it ~should~ be working as far as I can see

But the problem still persists.

---

### Post by speed32219 on 2008-09-11
You might need to add something to your asoundrc file in your home directory.  It is located in your home folder, you have to go to view and selcet hidden files or just cat .asoundrc from your home directory.  If nothing is there you may need to add a string but I am at work so I won't be able to provide that to you until later tongiht or tomorrow.

---

### Post by elwyn on 2008-09-12
> **speed32219 said:**
> If nothing is there you may need to add a string but I am at work so I won't be able to provide that to you until later tongiht or tomorrow.

Okay I'll have to wait I wouldnt know what to add :)

Thank you

---

### Post by speed32219 on 2008-09-12
OK, try adding this to your asoundrc file.  But first check it to see what is in there, it is a hidden file so it would be cat .asoundrc or vi .asoundrc from your terminal in your home directory. Found in applications/accessories. Cut and paste below and save.  

pcm.!default { 
	type hw 
	card 0 
	device 1 
}


Then right click on the speaker on top right of screen, make sure it isn't muted, then select preference and selct IEC958 or ALSA IEC958.  Then go to alsamixer in applications/sound&Video and make sure IEC958 **output** is on.  I have everything else muted that can be.  Now go to system/preference/sound and make sure everything is set to ALSA and then push the test buttons.  If that doesn't work try auto detect and see if you get any sound.
This will be only be stereo left & right across optical spidf, AC3 pass through is a whole other issue. (That is if it works)

---

### Post by at0mic on 2008-09-12
ull also want to tripple check your physical setup with your reciever. very easy to mess up the ins/outs/settings there.

---

### Post by elwyn on 2008-09-14
Its now working!
Im not sure what it was that fixed it, I had just written out a big post saying its still not working and help me more!

I have listed what I did to make it work here:

-in my home folder, enabled hidden files
-opened '.asoundsrc' in a text editor
-added the bit that was posted above ^^
so my .asoundsrc now looks like this:
```

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/elwyn/.asoundrc.asoundconf>
pcm.!default { 
type hw 
card 0 
device 1 
}

```

When I right click my volume icon, and click properties, I dont have the option mentioned above, so I left it on HDA NVidia (Alsa mixer)

A screenshot of my alsamixer settings are attached to this. (the SPDIF setting was on mute, even though I had unmuted it the other day, I dont think I read how to save alsamixer settings properly)

System> Preferences > Sound, I changed everything from Autodetect to Alsa

Thanks for your help everyone, and speed32219 for the clear steps!

---

### Post by speed32219 on 2008-09-14
The main thing was the code for the PCM and telling the system that card 0 device 1 was to be used, (card 0: NVidia [HDA NVidia], device 1: ALC882 Digital [ALC882 Digital]
),  from your first post displaying aplay -l command. So you basically just set that as your default sound path.  The rest is just unmuting and making sure volume levels are up.  Good job.

---

