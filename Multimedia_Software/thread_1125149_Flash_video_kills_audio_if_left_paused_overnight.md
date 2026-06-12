---
title: "Flash video kills audio if left paused overnight"
date: 2009-04-14
forum: Multimedia Software
---

### Post by MrNatewood on 2009-04-14
I am using Ubuntu 8.10 with Firefox 3.0.8 and flashplugin-nonfree 10.0.22.87ubuntu1~intrepid1 

If I leave a flash video in firefox paused for a long time(several hours), it kills sound functionality system-wide.

The only way I found to get sound working again is to reboot the system.

Is there any way to fix this?
Alternatively, is there a command I can ran so I can get the sound to restart without rebooting the computer?

some mplayer output when trying to play audio:
```
AO: [pulse] Failed to connect to server: Connection refused
[AO_ALSA] alsa-lib: pcm_hw.c:1321:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: Device or resource busy
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
[AO_ALSA] alsa-lib: pcm_hw.c:1321:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: Device or resource busy
[AO ARTS] can't connect to aRts soundserver
[AO ESD] esd_open_sound failed: Connection timed out
AO: [pulse] Failed to connect to server: Connection refused
[JACK] cannot open server
ao_nas: init(): Can't open nas audio server -> nosound
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
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

```

---

### Post by roblloyd on 2009-04-14
I'm running 8.10 (64-bit). I seem to be having the same problem. On occasion I will come back to my computer only to find that sound has stopped working. However, i have also fond the same problem when elisa or rhythmbox have been left running. This makes me think its more a alsa/pulseaudio problem than exclusively down to flash.

cheers in advance

---

### Post by amishphysicist on 2009-04-14
Same issue here.  Would love to just reset the audio server, rather than the whole box, if possible.

werrrd.

---

### Post by HotDogBunToo on 2009-04-14
Somewhat similar to my problem - except the sound stutters in my browser after it's open for afew hours.  And in my case it's resolved when I restart Firefox itself.  My system wide sound is unaffected from this though.  I do remember when I ran on PulseAudio I had no such issues with Flash sound and the browser - the downside was that Pulseaudio would go down so I would have to restart the process once in awhile.

---

### Post by amishphysicist on 2009-04-14
Tried restarting the sound server with this 
```
/etc/init.d/alsa-utils restart
```

Got some failures, then the restart seemed successful.  Unfortunately, all system audio was still broken.  Tried a killall on Firefox, but a restart still was the only thing to fix it.

---

