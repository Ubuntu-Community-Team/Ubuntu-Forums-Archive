---
title: "No audio in in VirtualBox"
date: 2011-08-28
forum: Multimedia Software
---

### Post by natomb on 2011-08-28
Hi,

I am running Mythbuntu 11.04 as host system and WinXP in a VirtualBox 4.1.2 instance. While audio output is working, audio input does not. On the host, every thing works fine (output as well as input). According to various searches, audio input and output shall work together since VirtualBox 3.1.something like a charm. Yet, mine is not.


I have attached the VirtualBox config file.

The output from the log file, which I suspect could be the cause is:

00:00:05.008 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:05.009 ALSA: Failed to open 'default' as ADC
00:00:05.081 ALSA: DAC frequency 44100Hz, period size 264, buffer size 1058
00:00:05.081 AC97: WARNING: Unable to open PCM IN!
00:00:05.081 AC97: WARNING: Unable to open PCM MC!
00:00:05.081 VM: Raising runtime error 'HostAudioNotResponding' (fFlags=0x0)
00:00:05.081 Console: VM runtime error: fatal=false, errorID=HostAudioNotResponding message="Some audio devices (PCM_in, PCM_mic) could not be opened. Guest applications generating audio output or depending on audio input may hang. Make sure your host audio device is working properly. Check the logfile for error messages of the audio subsystem"


Here is my asound.conf file:

pcm.!default {
  type plug slave.pcm {
    type hw card 1 device 3
  }
}


Thank you for assistance
  Bjoern

---

### Post by sylvaticus on 2011-10-04
hi, did u solve?
I had Virtualbox 4.0 and it was ok... on my virutal machine with VB guest addons 4.0 was still ok, but as I upgraded them to use the VirtualBox guest addons that matched the VirtualBox host (4.1) I got no sound at all..

---

### Post by natomb on 2011-10-10
Hi,

I could solve the problem. I had to change the asound.conf file to use different sound cards for input and output.

The output is going through HDMI to the television set, while the input comes via the AC97 soundcard. After adjusting the asound.conf it works. Here is what I have setup:

```

pcm.!default {
  type asym
  playback.pcm {
    type hw card 1 device 3
  }
  capture.pcm {
    type hw card 0 device 0
  }
}

```

---

