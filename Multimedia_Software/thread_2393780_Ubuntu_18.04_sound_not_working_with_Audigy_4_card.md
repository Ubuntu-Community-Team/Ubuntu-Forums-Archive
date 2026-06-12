---
title: "Ubuntu 18.04 sound not working with Audigy 4 card"
date: 2018-06-07
forum: Multimedia Software
---

### Post by chrisneedshelp on 2018-06-07
I have always had issues with Ubuntu and my sound card, but have always been able to get it working one way or another, but since updating to 18.04, nope, I cannot get it to work.  My output from 
```
sudo lspci -v
```
includes
> Multimedia audio controller: Creative Labs CA0108/CA10300 [Sound Blaster Audigy Series]
	Subsystem: Creative Labs SB0610 Audigy 4 Value
	Flags: bus master, medium devsel, latency 64, IRQ 22, NUMA node 0
	I/O ports at e800 [size=64]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: snd_emu10k1
	Kernel modules: snd_emu10k1

I believe that means I have the needed driver running and it recognizes my card.

Thanks in advance

---

### Post by chrisneedshelp on 2018-06-08
I guess I'm on my own with this one, time to go back to windows.

---

### Post by Yellow Pasque on 2018-06-09
Get more info. Maybe a simple mixer setting needs changed in alsamixer:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> **chrisneedshelp said:**
> I guess I'm on my own with this one, time to go back to windows.

Threats to go back to Windows less than 24 hours after you made the initial post do not make people want to help you...

---

### Post by chrisneedshelp on 2018-06-26
Apologies, and I completely understand, I was having a terrible day, and I've been so busy with work this is the first time I've been on my computer since then.  I tried your link and it asked me to run
```
  wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
``` 
which spit out 124 pages of information, not clear at all which of that is pertinent.  I ran the code twice, once to auto upload to the alsa server, and once to output locally and I coped the output into a new file.

---

### Post by Yellow Pasque on 2018-06-26
And the link to your info is... where?

---

### Post by chrisneedshelp on 2018-06-26
I am not exactly sure where it goes, that's why I ran it again storing locally and planned to post the output, but I was quite shocked at how much data it was.  Is there a way to know where it is sent to?

---

### Post by Yellow Pasque on 2018-06-26
When the script exits, it prints the link in the terminal, like:
```
Your ALSA information is located at http://www.alsa-project.org/db/?f=12345678
Please inform the person helping you.
```

If you still can't figure it out, please give the output of amixer command:
```
amixer
```

---

### Post by chrisneedshelp on 2018-06-26
The instructions indicated that I should have a link, but this was my complete output...

```
chris@chris-office:~$   wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2018-06-26 16:28:16--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org (www.alsa-project.org)... 77.48.224.243
Connecting to www.alsa-project.org (www.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-utils.git;a=blob_plain;f=alsa-info/alsa-info.sh [following]
--2018-06-26 16:28:17--  http://git.alsa-project.org/?p=alsa-utils.git;a=blob_plain;f=alsa-info/alsa-info.sh
Resolving git.alsa-project.org (git.alsa-project.org)... 77.48.224.243
Connecting to git.alsa-project.org (git.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-sh]
Saving to: &#8216;alsa-info.sh&#8217;

alsa-info.sh            [  <=>               ]  28.03K   139KB/s    in 0.2s    

2018-06-26 16:28:18 (139 KB/s) - &#8216;alsa-info.sh&#8217; saved [28707]

ALSA Information Script v 0.4.64
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at 
Please inform the person helping you.

```

There is no text after 'information is located at'...

---

### Post by chrisneedshelp on 2018-06-26
```
chris@chris-office:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 0 [0%] [-63.00dB] [off]
  Front Right: Playback 0 [0%] [-63.00dB] [off]
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
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB] [on]
  Front Right: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB] [on]
  Front Right: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB] [on]
  Front Right: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 18
  Mono: Playback 10 [56%] [0.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 17 [55%] [9.00dB] [off]
  Front Right: Capture 17 [55%] [9.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [off]
  Front Right: Capture 0 [0%] [-16.50dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Dynamic Power-Control',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'CD' 'Stereo Mix'
  Item0: 'Line'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'CD' 'Stereo Mix'
  Item0: 'Front Mic'
Simple mixer control 'Loopback Mixing',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Rear Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]

```

---

### Post by Yellow Pasque on 2018-06-26
That is odd. But anyway, what I was looking for was a control named "IEC958 Playback Switch" because that sometimes ends up enabled by default and then analog sound doesn't work. That must be on a different Audigy model though.

---

### Post by chrisneedshelp on 2018-06-29
Any other ideas?

---

### Post by LexxFan on 2018-07-04
Did you try the trigger "Audigy Analog/Digital Output Jack" near the end of alsamixer list?
Mine was muted by default, so that done the trick.
And if it's work for you too, don't forget to execute
> sudo alsactl store
to save the state.

---

