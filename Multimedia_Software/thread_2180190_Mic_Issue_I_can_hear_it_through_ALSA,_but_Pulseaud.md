---
title: "Mic Issue: I can hear it through ALSA, but Pulseaudio does not work"
date: 2013-10-11
forum: Multimedia Software
---

### Post by Dean_Rantala on 2013-10-11
Computer: HP Elitebook 6930p
OS: Ubuntu 13.10

Skype and Google Voice are a no-go right now.  "Microphone is not working".

Trying to adjust the levels via gnome mixer and pavucontrol seem to make no difference.

I can open alsamixer, however, and it works.. kinda.

So under alsamixer, I can un-mute the mic and change the volume level.  I know the hardware and alsa-driver is working because I can hear the mic sounds coming in through the speakers.  Turning up the mic gain too high even results in the typical high-squeal feedback.

I have 3 mic inputs: mic, doc mic and internal mic.  The one that actually works is the internal mic (built into the screen).  It may be worth noting: this laptop has stereo microphones (L+R) in each side of the screen.

It seems like pulseaudio knows there are 3 mic inputs, but is just not "connecting" the actual audio.  Moving the slider for each under pavucontrol and gnome mixer IS moving the coresponding mic slider under alsamixer - but the mute functions [under gnome mixer and pavucontrol] do NOT control the mute functionality.

It may be worth noting that I had this issue under 13.04 as well.

Here is a link to my alsa-info output: [http://www.uppercumberlandit.com/alsa-info.txt](http://www.uppercumberlandit.com/alsa-info.txt)

Many thanks in advance!

---

### Post by zblace on 2014-01-09
I have the same issue but with LUBUNTU :-/

---

### Post by zblace on 2014-01-09
I resolved mine on skype end... settings for mic input were not fall-backing to built-in mic, but random input.

---

### Post by Bucky Ball on 2014-01-09
*Thread moved to** Multimedia & Video**.*

> **zblace said:**
> I have the same issue but with LUBUNTU :-/

Then you should start a new thread rather than asking for support on this one (referred to as thread hijacking). It creates confusion and is unfair to the OP. ;)

@Dean_Rantala: Welcome. In Pulseaudio, presuming you are using Pulseaudio Volume Control, have you changed the device in the output tab to your device? Get an audio stream going with PAVolume Control open (play some sound), check in the playback tab. You should see controls for the audio stream there. Tweak with the audio device and make sure nothing in the output or playback tabs are muted. 

Install PAVControl in software centre or synaptics:

pavucontrol

... or via a terminal with:
```

sudo apt-get install pavucontrol
```

---

