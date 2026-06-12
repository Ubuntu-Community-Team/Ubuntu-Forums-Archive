---
title: "No audio via HDMI"
date: 2011-04-11
forum: Multimedia Software
---

### Post by natomb on 2011-04-11
Hello together,


I am setting up a MythTV environment to switch from Windows based MediaPortal (with a high number of disturbing bugs). Yet, I have three difficulties, which I want to discuss with you. They are:


- No audio via HDMI
- Video resolution seems to change during video playback (see [http://ubuntuforums.org/showthread.php?p=10663380#post10663380](http://ubuntuforums.org/showthread.php?p=10663380#post10663380))
- Channels cannot be found via DVB-S (see [http://ubuntuforums.org/showthread.php?p=10663378#post10663378](http://ubuntuforums.org/showthread.php?p=10663378#post10663378))


As you can see, I have created three posts to keep discussions focused.

Alltogether I have the following setup:

- AMD 5050e CPU
- 8 GByte RAM
- Biostar TA890GXE
- Samsung LE40M86BD, connected via HDMI (and only HDMI)
- Mythbuntu 10.10 with proprietary drivers installed
- Technisat Skystar HD2 DVB-S card (two times)


Now, here is the problem:

It does not matter what I try to playback, there is no sound. The TV set is NOT on mute, of course. I have invoked "alsamixer", the settings are as following:

```
Playback:
Master: 00 81
Headphon: 00
PCM: 100<>100
Front: 00 81<>81
Front Mi: MM
Front Mi: 0<>0
Surround: 00 0<>0
Center: 00 0
Center: 00 
LFE: 00 0
Side: 00 0<>0
Line: 00 0<>0
Mic: MM 0<>0
Mic Boos: 0<>0
S/PDIF: 00
S/PDIF D: 00

Capture:
Front Mic: 0<>0
Mic Boost: 0<> 0
S/PDIF: ------
Caputre: L R Capture 0<>0
Capture 1: L R Capture 0<>0
Input Sour: Mic
Input Sour: Mic

```When pressing "F6", I have the following options: default, HDA ATI SB, HDA ATI HDMI. Could it be the case that the default output device must be changed to HDMI? How would I achieve this?

For the HDA ATI HDMI the output is:

```
Playback:
S/PDIF: 00

```In the "Lautstärkeregelung" from the XFCE menu, I have selected "HDA ATI HDMI (Alsa mixer)" and enabled IEC958 (the only switch).


What could be the problem?

Thank you for assistance
  Bjoern

---

### Post by natomb on 2011-04-25
Hello,


problem solved by writing the following into (the new file) /etc/asound.conf:

pcm.!default { 
[LIST]
[*]type plug slave.pcm { 
[LIST]
[*]type hw card 1 device 3 
[/LIST]
} 
[/LIST]
}

---

