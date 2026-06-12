---
title: "No Sound in Audacity or Hydrogen. (Hardy, Dell Inspiron 1520)"
date: 2008-08-04
forum: Multimedia Software
---

### Post by demios on 2008-08-04
So I can get sound in rhythmbox and I get system sounds. Trying to play something in firefox from purevolume or myspace causes the browser to crash. Ability to record is intermittent -- didn't work for a while, then after the computer hibernated for a while it did. Messed around with settings in alsamixer for a while, didn't help.

running a Dell Inspiron 1520 with Hardy, which I installed yesterday. To try to fix this, I installed Alsa 1.0.17 a la [http://ubuntuforums.org/showthread.php?t=820959&](http://ubuntuforums.org/showthread.php?t=820959&) but no dice.

```
handicaptain@handicaptain:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


and in the listing from lspci -v,

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```

thanks a ton.

---

### Post by unebaguettesvp on 2008-08-05
i was also looking to get sound working with audactiy but if you are using hardy, you probably have pulseaudio installed and pulseaudio doesn't work with audacity:

[http://www.pulseaudio.org/wiki/PerfectSetup#Audacity](http://www.pulseaudio.org/wiki/PerfectSetup#Audacity)

so, i uninstalled pulseaudio:

[http://ubuntuforums.org/showthread.php?p=5512482#post5512482](http://ubuntuforums.org/showthread.php?p=5512482#post5512482)

now, audacity is working great and so is the sound from myspace. uninstall it at your own risk! you can always reinstall it but just be careful!

---

### Post by demios on 2008-08-05
wicked, I'll try that sometime I'm not on lunch break and see how it goes, thanks alot man.

---

### Post by demios on 2008-08-07
> i removed it successfully as well! in synaptic, i did a search for pulseaudio. i removed everything except for libasound2-plugins, libpulse0, and libsdl1.2debian-all. then i reinstalled esound to get my system sounds working again because i uninstalled pulseaudio-esound-compat (which wasn't working 100% to begin with). then i replaced my old .asoundrc and .asoundrc.asoundconf files. and everything worked!!! i had to change somethings back to alsa, like everything in System->Preferences->Sound. i also had to increase the volume on some channels in alsamixer.

i'm so glad i got rid of pulseaudio! none of my emulators worked, neither did audacity!

Edit: be careful of installing esound!!! caused gnome to freeze on another computer!

k, I know how to do everything there except replacing the two .asound files. How would I do that? I'm still relatively new to linux.

---

### Post by unebaguettesvp on 2008-08-08
if you don't have an asoundrc file already in your home directory, take a look at this:

[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

---

