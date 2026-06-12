---
title: "mplayer stops playing audio, error &quot;Failed to connect to server&quot;"
date: 2009-08-05
forum: Multimedia Software
---

### Post by jimhenry on 2009-08-05
I'm running Ubuntu 8.10 on a Dell Inspiron 15n laptop.  I've had a problem with sound not playing several times now. The first time was after Rhythmbox hung and I had to kill it -- I think it got confused because I had moved some files and directories that it was looking for (I didn't like the default directory structure it created when ripping CDs). After that, Rhythmbox would hang whenever I tried to play anything, and mplayer would give errors about a server being busy (see below). That problem went away after shutting down overnight and restarting next day; but the same or a simiilar problem recurred later, again went away after shutting down and restarting, and has again recurred after about 3 days uptime. I haven't used Rhythmbox since it started hanging, only mplayer.

mplayer is giving these errors:

```

AO: [pulse] Failed to connect to server: Connection refused
[AO_ALSA] alsa-lib: pcm_hw.c:1321:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: Device or resource busy
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
[AO_ALSA] alsa-lib: pcm_hw.c:1321:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: Device or resource busy
[AO ARTS] loading the aRts backend "/usr/lib/libartscbackend.la" failed
[AO ESD] esd_open_sound failed: Connection timed out
AO: [pulse] Failed to connect to server: Connection refused
[JACK] cannot open server
ao_nas: init(): Can't open nas audio server -> nosound
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
[AO_ALSA] alsa-lib: pcm_hw.c:1321:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
[AO SDL] Unable to open audio: No available audio device
[AO_ALSA] alsa-lib: pcm_hw.c:1321:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] alsa-lib: pcm_hw.c:1321:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
AL lib: alsa.c:344: Could not open playback device 'default': Device or resource busy
AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy
[OpenAL] could not open device
Opening /dev/dvb/adapter0/audio0
DVB AUDIO DEVICE: No such file or directory
AO: [null] 44100Hz 2ch s16le (2 bytes per sample)

```
I searched and found a thread here where someone counseled doing ```
sudo /etc/init.d/alsa-utils restart
``` to fix a similar sound problem; I tried that, and it hasn't helped. I also tried right-clicking the volume control and going through the options there, verifying that sound wasn't muted and so forth.  Someone in another thread suggested (for a different sound problem) starting alsamixer, tweaking the volume on each channel, and exiting; that didn't help a bit either.

lshw says I have this sound card, if that helps:

```

             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```The people posting in this thread back in April, [http://ubuntuforums.org/showthread.php?t=1125149](http://ubuntuforums.org/showthread.php?t=1125149), seem to have had similar if not identical problems, but no one posted a solution in that thread.

---

