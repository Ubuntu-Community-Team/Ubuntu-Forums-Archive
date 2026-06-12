---
title: "Alsa Midi Problems"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by electroconvulsive on 2006-11-16
I have a system running dapper. I have installed on this system a Delta 66 soundcard. When I try to open Hydrogen none of the audio drivers will open. From the terminal here is the error code.
[COLOR="Red"]
[ERROR]     AlsaAudioDriver     [connect] error in snd_pcm_hw_params_set_format: Invalid argument
[ERROR]     Hydrogen            [audioEngine_startAudioDrivers] Error starting audio driver [audioDriver::connect()]
[ERROR]     Hydrogen            [audioEngine_startAudioDrivers] Using the NULL output audio driver
[ERROR]     Hydrogen            [audioEngine_startAudioDrivers] m_pMainBuffer_L == NULL
[ERROR]     Hydrogen            [audioEngine_startAudioDrivers] m_pMainBuffer_R == NULL
[ERROR]     Hydrogen            [audioEngine_setupLadspaFX] nBufferSize=0
[ERROR]     NullDriver          [setBpm] not implemented yet
[/COLOR]
From MUSE I get

[COLOR="Red"]No superuser privileges, using system timer fallback
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
NO Config File </home/ric/.MusE> found
no locale <muse_en_AU.UTF-8>/</usr/share/muse/locale>
Trying RTC timer...
RtcTimer::setTimerFreq(): cannot set tick on /dev/rtc: Permission denied
  precise timer not available
Trying ALSA timer...
got timer = 12
QObject::connect: No such signal PartCanvas::horizontalScroll(int)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'unnamed')
Arranger::configChanged - no bitmap!
open projectfile: No such file or directory
starting with default template
  name2route: <alsa_pcm:playback_1> not found
  name2route: <alsa_pcm:playback_2> not found
Arranger::configChanged - no bitmap!
AlsaTimer::setTimerTicks(): requested freq 1024 Hz too high for timer (max is 250)
  freq stays at 250 Hz
Segmentation fault.[/COLOR]

Freeweelin crashes my Xserver when I try to open so it has now been uninstalled.
Ive also seen this error message before but i cant remember what I was launcing when it happened.

[COLOR="Red"]snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory[/COLOR]

Generally the internal MIDI and ALSA MIDI and audio components are missiong components.
snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
In one thread I read that you need alsa lib, thats a pity because it does not exist on the dapper repos.

Anyway if anyone can help me sort out this problem I would really appreciate it.

Personally I would rather not use jack at all because it has given me way too much trouble and I remenber being to run everything except rosegarden without it.

---

