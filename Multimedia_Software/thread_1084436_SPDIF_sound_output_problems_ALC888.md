---
title: "SPDIF sound output problems ALC888"
date: 2009-03-02
forum: Multimedia Software
---

### Post by gsf_atx on 2009-03-02
Hi all. I'm having trouble getting sound to come out properly on the SPDIF port of my new HTPC that I built. I installed Intrepid/v8.10.

I have made the appropriate modifications outlined in [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I have several issues:
1. Although I can get sound from flashplayer 10, I can't get sound from Rhythmbox, VLC (on videos that don't have AC3 streams) and even in the Systems/Preferences/Sound TEST buttons. 
2. When I play a video with an AC3 5.1 stream, the SPDIF passthrough works, but the sound stops and starts every x seconds. x=9 for one video, and x=5 for another. When this happens, the 2 lights on my AVR that indicate a DD stream go off and then on again. 

When I play something outlined in issue #1, the PCM light on my AVR lights up but there is no sound output.

I'm also finding that I cannot control the volume of the audio playing under flash. I can mute it in the volume control, can't change it though. Probably normal.

I can play sound normally through the headphone port, but it's only stereo out.

I've got the options in System/Preferences/Sound all set to use PulseAudio, and I modified /etc/pulse/default.pa to add a line:
"load-module module-alsa-sink device=hw:0,1"

As I'm using this system as an HTPC, not having surround capability is a showstopper.

Here's some info I've looked at:

```

gsf@htpc:/proc/asound$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[gsf@htpc:/proc/asound$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 57080 [87%] [on]
  Front Right: Capture 57080 [87%] [on]
gsf@htpc:/proc/asound$ man amixer
gsf@htpc:/proc/asound$ amixer info
Card default 'pulse'/'PulseAudio'
  Mixer name	: 'PulseAudio'
  Components	: ''
  Controls      : 4
  Simple ctrls  : 2
gsf@htpc:/proc/asound$ amixer -c 0 info
Card hw:0 'SB'/'HDA ATI SB at 0xfbcf4000 irq 16'
  Mixer name	: 'Realtek ALC888'
  Components	: 'HDA:10ec0888'
  Controls      : 33
  Simple ctrls  : 19
gsf@htpc:/proc/asound$ amixer scontents 
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 57080 [87%] [on]
  Front Right: Capture 57080 [87%] [on]
gsf@htpc:/proc/asound$ amixer -c 0 scontents
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 15 [48%] [-24.00dB] [on]
  Front Right: Playback 15 [48%] [-24.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 18 [58%] [-7.50dB] [on]
  Front Right: Playback 18 [58%] [-7.50dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 2 [67%]
  Front Right: 2 [67%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 17 [55%] [-21.00dB] [on]
  Front Right: Playback 17 [55%] [-21.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 21 [68%] [-15.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 16 [52%] [-22.50dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 19 [61%] [-18.00dB] [on]
  Front Right: Playback 19 [61%] [-18.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 18 [58%] [-7.50dB] [on]
  Front Right: Playback 18 [58%] [-7.50dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 14 [45%] [-13.50dB] [on]
  Front Right: Playback 14 [45%] [-13.50dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 27 [87%] [24.00dB] [on]
  Front Right: Capture 27 [87%] [24.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 14 [45%] [4.50dB] [on]
  Front Right: Capture 14 [45%] [4.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'

gsf@htpc:~$ cat .asoundrc
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
#</home/gsf/.asoundrc.asoundconf>
pcm.!default{
	type plug
	slave {
		rate 48000
		pcm "spdif"
		}
	}



```

Any suggestions are greatly appreciated. Thanks in advance.

---

### Post by boojeboy on 2009-03-02
I also have an HTPC, just built with Intrepid/v8.10. I haven't yet read through the link you posted (thanks btw).
I can get SPDIF test sounds but nothing else. I'd work on it now, unfortunately, humans are required to sleep or else we go insane.

---

### Post by gsf_atx on 2009-03-06
I hope this helps someone else. I'm not sure this solves my issue regarding SPDIF output of media that does NOT use the AC3 passthrough mode, but I think I know the cause of the problem. My AVR is a Denon AVR-3300 which has 24-bit DACs and does not support 32-bit digital PCM data (I think). I think the sound output is coming out as 32-bit data, which my receiver doesn't like. I found a post/bug report somewhere, sorry I don't remember the link, but it had an asound config file example to force 16-bit signed PCM data, I'm hoping. See below:

```

gsf@htpc:/etc/X11$ cat /etc/asound.conf 
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
#</home/gsf/.asoundrc.asoundconf>
pcm.!default{
	type plug
	slave {
		rate 48000
		pcm "spdif"
		format S16_LE
		}
	}

```

I hope this helps others, I'm not sure it helps me yet, I have some more testing to do...

---

### Post by alex2399 on 2009-03-06
I can't say I have exactly the same problem, since I do not use a receiver to decode SP/DIF, but a stereo 32/44/48 kHz DAC of my Philips DCC-900.

I also had alot of problems with non-functioning or garbled SP/DIF ouput. For instance when using VLC with a surround DVD it will set the SP/DIF output configuration to 192 kHz or something, rendering output useless for my DCC-900. After stopping VLC it will not revert to the previous setting, and there is no easy way of setting up the SP/DIF configuration.

But you can still set the ouput to your liking by using the terminal program "speaker-test". You can supply arguments to it like amount of channels, sampling rate etc to test speakers, but happily enough it also sets SP/DIF configuration to the values you use in this tool and the output retains this till another program changes it.

For inspiration, I use this command in the terminal to get the right sampling rate on the output for instance:
speaker-test -Dspdif -r44100 -c2 -f3000 -tsine

-Dspdif = output to use
-r44100 = sampling frequency/stream rate
-c2 = number of channels
f3000 = test signal frequency
tsine = waveform

To get a description of more options type 'speaker-test --h' or 'man speaker-test' and play around a little with the values and the output format, maybe it will help you.

---

### Post by gsf_atx on 2009-03-09
Hi Alex2399, thanks for the tip on speaker-test. I am able to output sound to analog and digital pcm outputs using this program. The output works properly with 16 or 32 bit signed data big/little endian, so the problem doesn't seem to be with my AVR not accepting 32 bit data. I'm able to get SPDIF pcm sound out of most programs, not sure exactly what has changed to allow this...

I'm still having the original major issue with AC3 passthrough stopping and starting every 4-9 seconds. I've found that if I Rewind/FF the video, the stop/start is NOT linked to specific times in the audio stream. It seems to stop/restart the stream 9 seconds after I begin playback.

When I play the video in totem, the sound plays fast (chipmunk) but stops and starts as well, as if the sound stream is not sync'd to the video stream because it's playing back at the wrong rate.

Any other suggestions are very welcome :)

---

### Post by gsf_atx on 2009-03-11
I've tried updating to ALSA 1.0.19 and now I don't get any sound via SPDIF. Nice. I've entered a bug at 

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4445](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4445)

Hope it gets sorted out. Interesting thing, this new version reports the chip as ALC1200 instead of ALC888.

---

### Post by gsf_atx on 2009-03-12
So I've resolved the no-spdif-output issue. I changed model=6stack_digout to model=6stack=dig and added other options to address kernel warnings, and it works OK.

The issue above seems to only affect VLC. Totem has another issue with AC3 passthrough where the sound plays fast and stops and starts. However, I got sound working with gmplayer, now that I know more about how sound devices are named, etc.

Here is the relevant section from /etc/modprobe.d/alsa-base:
options snd-hda-intel model=6stack-dig
options snd-hda-intel bdl_pos_adj=16
options snd-hda-intel position_fix=1
options snd-hda-intel power_save=0

1st line is probably what fixes the spdif issue
2nd and 3rd lines are for a kernel warning
4th line is trying to address the delay between when a system sound starts and when I hear it. It didn't help.

---

