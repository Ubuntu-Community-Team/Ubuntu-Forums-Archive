---
title: "S/PDIF Digital Out"
date: 2008-09-24
forum: Multimedia Software
---

### Post by spongemonkey on 2008-09-24
Hi everyone,

Have been having several problems with sound. I want to run all my sound through my S/PDIF connection on my on-board sound card to an external 5.1 receiver. In System > Preferences > Sound there are several options including nVidia CK804 and nVidia CK804 - IEC958. I understand nVidia CK804 - IEC958 is the S/PDIF digital out for my soundcard? But I don't get any sound out when I select this for the options. Is this even the way to set up an S/PDIF connection? There's also System > Preferences > Multimedia Systems Selector is that of any significance?

Thanks

EDIT

I can get stereo out via spdif now, but no Dolby Digital / DTS from DVDs.

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The second one there is the digital one that would transmit the DD/DTS stream to my receiver right?

With the first two setups of System>Preferences>Sound shown in the screenshots I get stereo sound, third I get nothing.

I'm trying to play a DVD with VLC and get surround sound with it. Have tinkered with just about every combination of settings in VLC I should think, which again leads me to believe that the device 0 isn't handling the DD/DTS streams. On the odd occasion I was given the option to select either "5.1" or "a/52 over spdif" as audio device (right clicking the picture in VLC while DVD is playing) -  the first gave me stereo, the second gave nothing.

Any help would be appreciated, I don't really know what I'm doing

---

### Post by spongemonkey on 2008-09-25
Bump

Haven't got any sound at all, anyone else setup a digital out for their audio?

---

### Post by jabeez on 2008-09-25
i'm using optical out, and I think I had to open alsamixer in a terminal and there is a switch in there I had to turn on (or was it off?). that's what I would try, just flip switches on/off with some audio playing and see what happens.

---

### Post by spongemonkey on 2008-09-25
No luck, I can get sound out of the headphone jack on the front of my box but no sound via the digital out

---

### Post by markbuntu on 2008-09-25
You should get:

gnome-alsamixer

It is far easier to use and understand than the alsa mixer in terminal. It may show you more switches and options to try. After you get it, you will find it in Applications/Sound & Video.

---

### Post by Patto77 on 2008-09-25
To get sound out of my digital I had to select IEC958 output.

---

### Post by tonyh6243 on 2008-09-26
That is what I had to do as well.

---

### Post by spongemonkey on 2008-09-29
Edited

---

### Post by spongemonkey on 2008-09-30
Trying to play a DVD through mplayer I get

Forced audio codec: hwac3
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 384000 bps, 48000 Hz
AUDIO: 48000 Hz, **2 ch**, ac3, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)

but shouldn't this be 6ch (5.1)? In alsamixer the number of channels is set to 6...

I've been googling ac3 passthrough for all different players, such as xine. They said to open the audio tab in settings and change the setup to 5.1 and simply enable passthrough, but there are no such options on the gui.

---

### Post by spongemonkey on 2008-10-01
Bump

---

### Post by markbuntu on 2008-10-01
VLC has that option I think.

---

### Post by MasterOfTheHat on 2009-11-25
Patto77, you are the man! Needed to turn up IEC958 output in alsamixer.

---

