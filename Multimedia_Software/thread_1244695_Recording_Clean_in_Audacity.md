---
title: "Recording Clean in Audacity"
date: 2009-08-19
forum: Multimedia Software
---

### Post by solaralchemy on 2009-08-19
I have been using audacity to record streaming radio and audio and so far it has been working pretty good, but im a perfectionist and have noticed a slight warbelley echo like sound in playback....it doesn't seem like the bigest problem yet its still anoying.
I was wondering if anybody else using audacity to record streaming has a set up to record the cleanest sound possible using audacity. Like what should the volume settings be in input? What should all the other setting be?
Thanks for any suggestions

---

### Post by bobince on 2009-08-20
I haven't experienced that problem in Audacity, but in general it's better to record streams in their original digital format than to output them to the sound system, record back off the sound system and re-encode (to MP3 or whatever). That way there is no loss of quality.

Tools like mplayer and VLC's &#8216;Convert/Save&#8217; option will allow you to dump a stream to disc as well as listening to it. SHOUTcast/Oddcast streams can even be saved with something as simple as wget. In the case of web-embedded players you'll have to extract the real stream URL from the player first. View Source or the Firefox DOM Inspector can be helpful for this.

---

### Post by mcduck on 2009-08-20
I recommend using streamtuner/streamripper to save the audio streams, this will save the stream exactly as it's broadcasted instead of re-encoding all the data (which will definitely decrease the sound quality).

In addition Streamripper will separate different songs automatically, and name them correctly, if the stream includes song names.

(Streamripper is a command-line program , but it integrates into Stramtuner which is a graphical tool for browsing internet radio streams)

---

### Post by hoscha on 2009-09-07
> **solaralchemy said:**
> I have been using audacity to record streaming radio and audio and so far it has been working pretty good, but im a perfectionist and have noticed a slight warbelley echo like sound in playback....it doesn't seem like the bigest problem yet its still anoying.
I was wondering if anybody else using audacity to record streaming has a set up to record the cleanest sound possible using audacity. Like what should the volume settings be in input? What should all the other setting be?
Thanks for any suggestions

I would like capture what comes out of my sound card "like out of speakers" but i cant get my setting to pick up the sound. I have no mic.  But i heard you can use ur input as your output or something. Any help?? Ubuntu 9.04 is what i am running.

I have tried using every combination possible switching them in the Audio I/O.

In the Audacity Audio I/O options: Play Device has: ALSA: HDA NVidia: Conexant Digital (hw:0,1), ALSA: iec958, ALSA: spdif, ALSA: pulse, ALSA: default.  Underneath the Playback device option list is says.. Using: Portaudio v19.  As for the Recording device area: LSA: HDA NVidia: Conexant Digital (hw:0,0), ALSA: pulse, ALSA: default, OSS: /dev/dsp.  Would it matter if i didnt have a FFmpeg Library Version: FFmpeg library not found?? 

As for the computer Volume Control Device list: HDA NVidia (Alsa mixer), Conexant CX20561 (Hermosa) (OSS Mixer), Playback: HDA NVidia - CONEXANT Analog (PulsoAudio Mixer), Capture: Monitor of HDA NVidia - CONEXANT Analog (PulsoAudio Mixer), Capture: HDA NVidia - CONEXANT Analog (PulsoAudio Mixer).

==============================
Default capture device number: 5
Default playback device number: 5
==============================
Device ID: 0
Device name: ALSA: HDA NVidia: CONEXANT Analog (hw:0,0)
Input channels: 2
Output channels: 0
Low Input Latency: 0.011610
Low Output Latency: -1.000000
High Input Latency: 0.046440
High Output Latency: -1.000000
Supported Rates:
==============================
Device ID: 1
Device name: ALSA: HDA NVidia: Conexant Digital (hw:0,1)
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    44100
    48000
    96000
==============================
Device ID: 2
Device name: ALSA: iec958
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    44100
    48000
    96000
==============================
Device ID: 3
Device name: ALSA: spdif
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    44100
    48000
    96000
==============================
Device ID: 4
Device name: ALSA: pulse
Input channels: 32
Output channels: 32
Low Input Latency: 0.011610
Low Output Latency: 0.011610
High Input Latency: 0.046440
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
    192000
==============================
Device ID: 5
Device name: ALSA: default
Input channels: 32
Output channels: 32
Low Input Latency: 0.011610
Low Output Latency: 0.011610
High Input Latency: 0.046440
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
    192000
==============================
Device ID: 6
Device name: OSS: /dev/dsp
Input channels: 16
Output channels: 0
Low Input Latency: 0.011610
Low Output Latency: 0.000000
High Input Latency: 0.046440
High Output Latency: -0.000000
Supported Rates:
==============================
Selected capture device: 5 - 
Selected playback device: 5 - 
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
    192000
Unable to open Portmixer

---

