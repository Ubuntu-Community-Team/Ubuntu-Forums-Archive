---
title: "No sound EXCEPT with .mkv files...HELP!"
date: 2008-11-11
forum: Multimedia Software
---

### Post by Dark Hornet on 2008-11-11
ok..I am having a very odd issue...ever since the update last night I guess, the ONLY file format I seem to be able to get sound with is .mkv...I get no sound with .avi, .mp3, etc....nothing...and I have tried Amarok, movie player, VLC (which I use to play the .mkv files, and that works)...the drum sounds don't even play when I boot up.  Keep in mind that everything was working the other day perfectly.  Oh and in addition, flash plays fine, but no sound from that as well.

Please someone help.

thanks,
Darkhornet

Edit: I am running 8.04, and I seem to get sound on SOME .avi files but not all.

---

### Post by Dark Hornet on 2008-11-12
Anyone?

Edit --ok a new development....I have sound on everything through my headphone jack (mp3, .avi, .mkv, etc) and sound with .mkv through my speakers.  This is a very odd issue!  Someone please help

---

### Post by Feelkarma on 2009-09-20
Hi,

Did you ever get any luck with solving this?

I am new to Ubuntu and have the same strange problem, recently installed jaunty, I get (fantastic) surround sound when playing mkv files but nothing with audio files such as mp3. The strange thing is that it used to work perfectly but somehow sound stopped working after a restart. Tried uninstalling all gstreamer and reinstaling, undinstalling flash plugin, tried with VLC and even installed Amarok, no luck.

My config:
M/B: Asus M3N H HDMI with Phenom CPU
2gb Kingston PC8500 Memory
Pioneer DVD writer
Samsung 500 gb HD

I have dual boot Windows XP / Jaunty and intend to get rid of XP as soon as everything is working under Ubuntu ;-)

Thanks

---

### Post by raboofje on 2009-09-20
Could you post the output of 'aplay -l'?

I'm not too familiar with surround-sound setups, but one thing i could imagine is this: supposed your 'surround' card represents itself as 8 outputs: 2 for your headphones, 5+1 for your speakers. A 'dumb' audio player playing a stereo file might just output to the first 2 outputs, in your case being the headphones. 

You might be able to configure your player to play though the surround speakers instead of just the first pair it finds.

---

### Post by Feelkarma on 2009-09-20
Hi, and thanks for the quick reply!

Here it is:

**** List of PLAYBACK Hardware Devices ****
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

New issue: I now get the following error message when trying to open volume control (I reinstalled pulseaudio, but no change): "Failed to start Volume Control: Failed to execute child process "gnome-volume-control" (No such file or directory)"

Thanks again

---

### Post by raboofje on 2009-09-20
> **Feelkarma said:**
> card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Hmm ok, 1 device for the analog outputs and 1 for the digital. Not sure what's going on then, sorry.

> I now get the following error message when trying to open volume control (I reinstalled pulseaudio, but no change): "Failed to start Volume Control: Failed to execute child process "gnome-volume-control" (No such file or directory)

The 'search the contents of packages' feature on [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) tells us gnome-volume-control is in the gnome-media package, do you have that installed?

---

### Post by Feelkarma on 2009-09-20
Last problem solved by reinstalling Ubuntu-desktop. Not sure how I managed to screw that up, I'm learning as I'm going ;)

---

### Post by Feelkarma on 2009-09-20
It is weird, I get sound through earphones though... Thanks for your help anyways!

---

### Post by Feelkarma on 2009-09-20
Ok, this solved it somehow (unless it's pure luck) [http://xbmc.org/forum/showthread.php?t=35901](http://xbmc.org/forum/showthread.php?t=35901)
Thanks again

---

### Post by winecurmudgeon on 2009-12-12
This was very weird. My sound had more or less worked, and then it stopped. I used the sudo alsa force-reload in the link, and that seems to have done the trick.

---

