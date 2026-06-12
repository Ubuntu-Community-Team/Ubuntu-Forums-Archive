---
title: "Problems with USB Audio card"
date: 2009-10-24
forum: Multimedia Software
---

### Post by Vi3GameHkr on 2009-10-24
Hi, I'm having some problems getting my GWC USB 5.1 Surround Audio Adapter to work (AA1500)

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The second card is the one I want to use but I haven't been able to set it to default.

```

$ cat /proc/asound/modules
 1 snd_hda_intel
 2 snd_usb_audio

```

I was checking out the sticked Comprehensive Sound Problems thread so I opened up the alsa-base

```

sudo nano /etc/modprobe.d/alsa-base

```

And it was completely empty but I added the following two lines:

```

options snd_usb_audio index=0
options snd_hda_intel index=1

```

But the default sound card is still the onboard one.  All I think I need to do is change the default sound card, but I can't figure out how and I've tried a few things.  Also in System > Preferences > Sound, I found that if I selected "USB Audio USB Audio OSS" and pressed test, I heard a loud beep from my speakers but when I select "USB Audio USB Audio (ALSA)" and press test then I get the following error message:
"audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback."

I hope I have provided enough information for someone to easily see what is going on, and I also hope that I haven't simply skimmed over a very simple solution.

Thanks in advance,
Vi3GameHkr

---

### Post by kostkon on 2009-10-24
You need to install the PulseAudio Device Chooser utility (using Synaptic). More info [here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

