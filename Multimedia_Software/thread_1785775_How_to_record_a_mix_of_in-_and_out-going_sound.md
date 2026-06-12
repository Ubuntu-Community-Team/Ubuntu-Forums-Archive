---
title: "How to record a mix of in- and out-going sound?"
date: 2011-06-18
forum: Multimedia Software
---

### Post by barna on 2011-06-18
Hi,
I discovered recently how pavucontrol can be used for example to record the output of one application by another application. 
But I don't find the way to record a mix of two streams. For example, I would like to record a conversation in Skype.

I have set playback and recording for skype to 'Clear Chat Comfort USB Headset Analog Stereo', i.e. Skype is now using my headset, that's fine.

However, when starting audacity, in the Recording tab of pavucontrol I can only select from the following list for 'ALSA plug-in [audacity]'
- Monitor of internal audio analog stereo (this records the output sent to the analog speaker)
- Internal Audio Analog STereo (this records from the built-in microphone)
- Clear Chat Comfort USB Headset Analog Mono (this records from the microphone of the usb headset)
- Monitor of Clear Chat Comfort USB Headset Analog STereo (this records the output sent to the headset)

Unfortunately, none of these options can record at the same time the two-way communication going through skype (or going through my headset), i.e. what I say into the microphone and what I hear in the earphone.
Is this possible?

Thanks

---

### Post by Gerbiler on 2011-09-15
I have a very similar problem. I'm just starting up some minecraft screen-casts with ffmpeg. But I can't figure out how to record minecraft sounds as well as my mic. It's the same basic problem, I can't figure out how to use Pulse Audio to mix two inputs.

---

### Post by dniMretsaM on 2011-09-15
Possibly two instances of the same program, each one recording from a different source? Never tried it, but it might work.

---

### Post by Drevious on 2011-09-15
Try this first:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)



Second option:

[http://ubuntuforums.org/showthread.php?t=119575](http://ubuntuforums.org/showthread.php?t=119575)

---

### Post by shantiq on 2011-09-17
> **barna said:**
> Hi,
I discovered recently how pavucontrol can be used for example to record the output of one application by another application. 
But I don't find the way to record a mix of two streams. For example, **I would like to record a conversation in Skype.**

I have set playback and recording for skype to 'Clear Chat Comfort USB Headset Analog Stereo', i.e. Skype is now using my headset, that's fine.

However, when starting audacity, in the Recording tab of pavucontrol I can only select from the following list for 'ALSA plug-in [audacity]'
- Monitor of internal audio analog stereo (this records the output sent to the analog speaker)
- Internal Audio Analog STereo (this records from the built-in microphone)
- Clear Chat Comfort USB Headset Analog Mono (this records from the microphone of the usb headset)
- Monitor of Clear Chat Comfort USB Headset Analog STereo (this records the output sent to the headset)

Unfortunately, none of these options can record at the same time the two-way communication going through skype (or going through my headset), i.e. what I say into the microphone and what I hear in the earphone.
Is this possible?

Thanks


This **[here]("http://atdot.ch/scr/download/")** works really well and easy to use

---

