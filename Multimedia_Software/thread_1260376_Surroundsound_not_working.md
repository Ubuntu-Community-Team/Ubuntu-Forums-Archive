---
title: "Surroundsound not working"
date: 2009-09-07
forum: Multimedia Software
---

### Post by getekha on 2009-09-07
Hi, 

I've bought a 5.1 soundsytem but I can't seem to get it to work with my linux htpc.

I'm running 9.10 atm and stereo works fine.



I'm using the onboard soundcard on GA-MA74GM-S2, Realtek ALC888

It only has 3 ports, line-in, line-out and mic. What I just can't seem to do is tell my system to use mic and line-in as output channels for the backspeakers and front/lfm. I've googled, searched forums and read a dozen guides but I just can't seem to find it.

My method of testing the system is 

speaker-test -Dplug:surround51 -c6 -l1 -twav

and the only port that is outputting sound at the moment is line-out.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

edit: messed up the code tag

---

### Post by HappyFeet on 2009-09-07
If it only has 3 ports, it is not surround sound capable. For example, my onboard sound has the 3 ports that you have, plus 3 others (grey, black, and orange), for surround output.

What led you to believe that yours is surround capable?

---

### Post by Lucky75 on 2009-09-07
> **HappyFeet said:**
> If it only has 3 ports, it is not surround sound capable. For example, my onboard sound has the 3 ports that you have, plus 3 others (grey, black, and orange), for surround output.

What led you to believe that yours is surround capable?



It's completely possible to have some form of surround sound with 3 ports (including the mic/other). That's actually standard. I've done it, as my system is the same, but I can't for the life of me remember. It was a real pain to do before I got it working. I think I followed the surround sound guide in this forum.

The first thing to do is edit your */etc/pulse/daemon.conf* file.
Set **default-sample-channels = 6**

Then you need to go into the alsa mixer and make sure the surround sound is unmuted. I got it working in 9.04, don't know about how it works in 9.10

---

### Post by getekha on 2009-09-07
I*'*ve already edited the */etc/pulse/daemon.conf *without any luck

And as far as I can tell nothing is muted in the alsamixer..

Also I've got the surroundsound working on windows once I found out how to change the mic/line-in to work as outputs instead, so it's defently a working 5.1 system...

---

### Post by dano1 on 2009-09-08
check for switches(or show switches) in your payback device. Do you have the correct drivers?

---

### Post by getekha on 2009-09-08
> **dano1 said:**
> check for switches(or show switches) in your payback device. Do you have the correct drivers?

As far as I can tell I have the correct drivers (I am getting stereo sound)

I installed the drivers using the alsa upgrade script  ([http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810))

I've checked for "switches" but I can't find any. Anyone got any pointers?

---

### Post by dano1 on 2009-09-09
open your playback settings, , click preferences. This will show you what you want to be visible including any switches  for mic/rear speakers etc...

---

### Post by getekha on 2009-09-09
> **dano1 said:**
> open your playback settings, , click preferences. This will show you what you want to be visible including any switches  for mic/rear speakers etc...

What are you referring to when you say "playback settings", when I right click the sound icon in the top right I can chose "Sound Preferences" but I can't find anything useful in there. I've also tried the gnome alsa mixer without finding anything usefull

---

### Post by dano1 on 2009-09-12
sorry bad instructions. left click icon,go to volume c oontrol. from pulldown menu find your xxx(alsamixer device). Check for "options" tab see mine for a cmi sound card:

/home/dan/Desktop/Screenshot.png

enable options from the dropdown menu. If that doesn't do it click preferences, select tracks to be visible, and check as needed, then configure in your settings see:

/home/dan/Desktop/Screenshot-Volume Control: C-Media CMI8738 (Alsa mixer).png

hth, danny

---

