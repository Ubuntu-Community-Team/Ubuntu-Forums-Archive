---
title: "sound problems in intrepid"
date: 2009-04-30
forum: Multimedia Software
---

### Post by bootdoc on 2009-04-30
Just installed intrepid on hp pavillion entertainment pc. I have sound from most audio apps coming through the usb headset but not the onboard speakers.  Mplayer and totem play dvds and audio comes through headset also.  Dragon player audio comes through the pc speakers and usb speakers.  when dragon player is running there are no output streams in PAD.  When amarok is playing PAD shows amarok audio stream on simultaneous output to alsa pcm on front:1 blah blah.

There is no choice for hda intel alc268 analog alsa in PAD.  

I have to say I have not run into this problem before.  Pulse works great on my desktop.

Pulse audio device chooser>volume control>output devices shows the simultaneous output... and alsa pcm on front:1 (usb audio via dma)

---

### Post by psyke83 on 2009-04-30
First, follow my PulseAudio guide to ensure your configuration is clean.

Second, see [this]("http://ubuntuforums.org/showpost.php?p=7181418&postcount=1246") post for information on how to configure PulseAudio to use a "hidden" ALSA device which otherwise wouldn't be available via PulseAudio Volume Control.

---

