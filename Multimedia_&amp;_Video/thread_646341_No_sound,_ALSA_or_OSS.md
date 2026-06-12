---
title: "No sound, ALSA or OSS"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by Tarmael on 2007-12-21
Hey,

Dunno what happened.

Sound isn't working.

Here is a sample from mplayer when trying to listen to any music file.

```

MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tank.mp3.
File not found: 'tank.mp3'
Failed to open tank.mp3.


Exiting... (End of file)
tarmael@Melchior:/media/sdb1/MUSVETHRNb$ mplayer Tank.mp3
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Tank.mp3.
Audio file file format detected.
Clip info:
 Title: Tank!
 Artist: The Seatbelts
 Album: Cowboy Bebop OST
 Year: 
 Comment: 
 Track: 1
 Genre: Unknown
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
alsa-lib: pcm_hw.c:1242:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
alsa-lib: pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
alsa-lib: pcm_hw.c:1242:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
alsa-lib: pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
[AO ARTS] loading the aRts backend "/usr/lib/libartscbackend.la" failed
W: main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
[AO ESD] esd_open_sound failed: No child processes
E: authkey.c: failed to open cookie file '/home/tarmael/.pulse-cookie': Permission denied
E: authkey.c: Failed to load authorization key '/home/tarmael/.pulse-cookie': Permission denied
AO: [pulse] Failed to connect to server: Connection refused
ao_nas: init(): Can't open nas audio server -> nosound
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
alsa-lib: pcm_hw.c:1242:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
alsa-lib: pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
[AO SDL] Unable to open audio: No available audio device
Opening /dev/dvb/adapter0/audio0
DVB AUDIO DEVICE: No such file or directory
AO: [null] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...


```

Please help!

---

### Post by minus198 on 2007-12-22
I have the same issue.

---

### Post by duelol on 2007-12-26
Me too.

---

### Post by oskar2000 on 2008-02-09
bump.
me too - just now.
Same error log.

Problem resolved after logging in again.

---

### Post by Dandeloreon on 2008-02-09
can you post the output of the command...
```

aplay -l

```

and also a copy of the following 2 files:
/etc/asound.conf
~/.asoundrc

---

### Post by oskar2000 on 2008-02-10
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
I don't have an asound.conf in /etc - couldn't locate it either. There's an asoundconf binary in /bin/usr.

.asoundrc:
```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/roman/.asoundrc.asoundconf>
```

---

