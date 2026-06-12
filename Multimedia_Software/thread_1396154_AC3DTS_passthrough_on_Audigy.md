---
title: "AC3/DTS passthrough on Audigy"
date: 2010-02-01
forum: Multimedia Software
---

### Post by edwardof on 2010-02-01
I am unable to get passthrough audio working on my Mythbuntu box. I'm using an Audigy with firewire (SB0230) because I only have 3 PCI slots and the RAID card and video card are taking up the other two. 2-channel digital out is working fine. I've tried using various asound.conf files as well and have not had any success.

Here's as much info as I've gathered:
```

efoster@MythTV:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````

efoster@MythTV:~$ aplay -L
default:CARD=Audigy
    Audigy 1 [Unknown], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Audigy,DEV=0
    Audigy 1 [Unknown], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy,DEV=0
    Audigy 1 [Unknown], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy,DEV=0
    Audigy 1 [Unknown], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
surround40:CARD=Audigy,DEV=0
    Audigy 1 [Unknown], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy,DEV=0
    Audigy 1 [Unknown], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy,DEV=0
    Audigy 1 [Unknown], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy,DEV=0
    Audigy 1 [Unknown], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=Audigy,DEV=0
    Audigy 1 [Unknown], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

``````

efoster@MythTV:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: raw midi
  6: [ 0- 0]: raw midi
  7: [ 0- 3]: digital audio playback
  8: [ 0- 2]: digital audio playback
  9: [ 0- 2]: digital audio capture
 10: [ 0- 1]: digital audio capture
 11: [ 0- 0]: digital audio playback
 12: [ 0- 0]: digital audio capture
 13: [ 0]   : control
 14: [ 0- 2]: hardware dependent
 15: [ 0- 2]: raw midi
 16: [ 0- 3]: raw midi

```So it seems that 0.3 would be the digital output, but here's what happens when I try to use it:
```

efoster@MythTV:~$ aplay -D hw:0,0 /mnt/dvds/a.wav
Playing WAVE '/mnt/dvds/a.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
^CAborted by signal Interrupt...
efoster@MythTV:~$ aplay -D hw:0,3 /mnt/dvds/a.wav
Playing WAVE '/mnt/dvds/a.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
aplay: set_params:974: Access type not available

``````

efoster@MythTV:~$ mplayer -ac hwdts -ao alsa:device=hw=0.3 /mnt/dvds/Prelude.wav
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team

Playing /mnt/dvds/Prelude.wav.
Audio only file format detected.
==========================================================================
Forced audio codec: hwdts
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to DTS, 1411200 bps, 44100 Hz
AUDIO: 44100 Hz, 2 ch, ac3, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [hwdts] afm: hwac3 (DTS through S/PDIF)
==========================================================================
[AO_ALSA] alsa-lib: conf.c:3843:(parse_args) Unknown parameter AES0
[AO_ALSA] alsa-lib: conf.c:3969:(snd_config_expand) Parse arguments error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM hw:0,3,AES0=6
[AO_ALSA] Unable to set access type: Invalid argument
Failed to initialize audio driver 'alsa:device=hw=0.3'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


Exiting... (End of file)

```If I send the output to 0.0 I get 2 channel sound over SPDIF, if I force hwdts or hwac3 to 0.0 I get static. I get no change in behavior if I change the optical raw setting in alsamixer.

Does anyone have any idea? I'm new to Mythbuntu, but I've been scouring google for some insight on this problem and I haven't found anything that helps.

---

### Post by _zifban on 2010-04-06
I just had a similar problem and finally found the solution that worked for me.
After trying to do put the iec958 into non-audio mode with "iecset audio off", 
which didn't change the mode in my system, I found someone who had
a similar problem and who had found a solution to it.

All I had to do was to disable the equalizer with alsamixer. After that ac3 passthrough
with mplayer worked again. I have Aureal Vortex au8830 sound card and had
just updated my kubuntu, which might have modified the mixer settings.

---

### Post by edwardof on 2010-04-18
Well I figured it out. The digital output jack actually has more than one digital out. I was connected to the rear channels' PCM output because I was on the wrong channel of my stereo 3.5mm to stereo RCA adapter. Because 4 channel stereo was turned on, I was getting the same audio as the fronts. As soon as I switched to pass-through, the rear digital channels go silent as all the audio is pumped through the front channels. A stupid mistake, but I didn't know there was more than one digital output in the same 3.5mm jack, so when I got audio I assumed it was right. Didn't end up needing any additional config beyond turning on pass-through in the audio options in MythTV.

---

