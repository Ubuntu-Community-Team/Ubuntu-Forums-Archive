---
title: "Pulse Audio/ALSA and VirtualBox"
date: 2012-12-10
forum: Multimedia Software
---

### Post by mastermindg on 2012-12-10
I'm running 12.04 64bit with VirtualBox 4.2.4 and I finally have audio playing from VirtualBox (Windows 7) using the ALSA driver. My problem now is that I'm not getting any audio from any other sources locally in Ubuntu (VLC, Firefox, etc). I've installed Pulse Audio Manager and I'm looking at the modules/sources and nothing is muted.

NOTE: I am running VirtualBox as root.
NOTE: When I attempt to run mplayer as root I get the following:

> AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
Home directory /home/ken not ours.
[AO_ALSA] alsa-lib: pcm_hw.c:1293:(snd_pcm_hw_open) open '/dev/snd/pcmC0D0p' failed (-16): Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: Device or resource busy
Failed to initialize audio driver 'alsa'
[AO SDL] Samplerate: 48000Hz Channels: Stereo Format floatle
[AO SDL] using aalib audio driver.
[AO SDL] Unsupported audio format: 0x1d.
[AO SDL] Unable to open audio: No available audio device
Failed to initialize audio driver 'sdl:aalib'
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...



How can I use ALSA with VirtualBox and still get PulseAudio to play locally?

---

### Post by mastermindg on 2012-12-10
I'm not sure what solved the problem but after restarting VirtualBox and pulseaudio service a couple of times I now have audio in VLC.

Scratch that...now I don't have any audio in VirtualBox.

---

