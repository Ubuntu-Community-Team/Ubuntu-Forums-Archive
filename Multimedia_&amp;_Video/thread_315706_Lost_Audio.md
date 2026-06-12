---
title: "Lost Audio"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by lakelovers on 2006-12-09
I running Ubuntu 6.06 on a Dell, Dimension 2300 with an integrated sound card and have lost the sound. I didn't notice the problem until today when I tried to download mp3 music. I've checked the volume controls, mute settings, and cords from speakers to the computer. The speakers are turned on. Under *Preferences* I have Intl 82801DB-ICH4 (Alsamixer), and Alsa is installed though I'm not sure whether I have the correct settings on it. I've closed the *lock* on most or all elements. Is that correct? What is the significance of the *red dots* at the top of some elements? I didn't see *Help* on the Alsamixer. I'll appreciate any and all suggestions.
Jerry

---

### Post by lakelovers on 2006-12-10
I've tried navigating "Comprehensive Sound Problems" but I guess I'm not enough of a computer whizz to understand. I tried "# sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
# Reinstall those same packages" but I got the error meassage:Invalid operation purge.

So then I stuck my neck out and tried an install: sudo apt-get install linux-sound alsa-base alsa-utils. This is what I got:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-sound

When I look at: aplay -l, I get see my sound card:

List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I still have no sound and I don't know where I go from here.

---

### Post by nrgtek on 2006-12-11
I'm in the same boat:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Robert Leithe on 2006-12-12
I lost my sound just now. I hooked my Dell Inspiron 9300 up to a projector and watched a movie.
I ran a shutdown on both computer and projector. Went shopping, and came back and turned everything back on. No sound.
On the same note, I also had problems starting the GUI. Had to start in recovery mode and copy back a previous copy of xorg.conf. However, that copy was recent, and the sound was working fine at the time I made the copy.

I've ran through several programs to see if I hade muted the sound somehow, but cannot find anything. The volume is turned up to max everywhere I can find a volume control. Have tried both internal speakers and earphones - no sound.

What gives?

Sincerely

EDIT: Found the "missing link" after some more looking around (please forgive a Linux novice :)
I had to open the Volume Control and "unmute" some of the choices available there.

---

### Post by scrooge_74 on 2006-12-12
Go the easy way for you guys,get into synaptic

Find all alsa packages and uninstall them
Then install them again.  I few post I ahve seen lately deals with a similar problems.

Maybe this way you can reset your audio,it helped me once

Good luck

---

### Post by lakelovers on 2006-12-16
I reinstalled all the alsa apps, but i get this error message at the end of the install:"Alsabase subprocess posst-installation script returned error exit status 1." Any idea what this is and what I do about it?

---

### Post by dorusone on 2007-01-31
Had also no sound . Rebooting didnot fix the problem.
Then i booted XP which had sound.
Rebooted Ubuntu again and sound again.
I really like Ubuntu and XP did like it too.......... LOL

---

