---
title: "No multimedia sound in KDE"
date: 2009-09-23
forum: Multimedia Software
---

### Post by jfenn2199 on 2009-09-23
I've added KDE after an install of Jaunty, everything is working perfectly in Gnome, but in KDE I have sound at start up and shutdown but when I attempt to listen to music or go to a flash page I have no audio what so ever.

First and foremost I'm running on a Dell GX1 with the on board sound card which uses the CS4236B sound card.  I've tried changing the Master Channel in KMix and nothing seems to work

When I run aplay -l this is what's output

```

card 0: CS4236B [CS4236B], device 0: WSS [CS4236B]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

Any help would be greatly appreciated

---

### Post by jpthompson23 on 2009-10-06
I have this exact same problem in Kubuntu.  I hear the startup/shutdown sounds, and I can go into the multimedia control panel and hear the test music on HDA Intel (ALC1200 Analog) but I can't get any audio in firefox or mp3 players.

Someone please figure this out.

---

### Post by kbm on 2009-10-07
I started out with similar problems.  The first thing that I had to do was add some driver options to my modprobe.conf file.  Since things worked in Gnome, I'm guessing you are past that type of issue though.

The second thing I had to do was tell the KDE sound system (Phonon (sp?)) to use PulseAudio as it's output device for everything.

Go into System Settings -> Multimedia (I think that's the wording anyway).  Change your sound settings for all outputs to put PulseAudio first.  That did it for me.  Items that used to make sound but caused a 'sound device X not working, failing over to Y' message stopped showing errors and items that used to make no sound at all started working just fine.

Hope it helps.

Also, I've also had my mixer settings pull the PCM channel down to 0 (or mute, can't remember).  So even when I thought my volume was up, the input channel had been turned off so check that as well.

---

