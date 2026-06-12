---
title: "My mic stopped working tonight"
date: 2011-07-23
forum: Multimedia Software
---

### Post by perfwill on 2011-07-23
I'm totally confused and can't understand what happened.
Last night my mic was still working well, but tonight it doesn't work. Note that the sound output is still working normally, just the mic has the problem.
My machine is on lubuntu with alsa. I checked the "mic" volume in alsamixer and it's ok. And I don't turn on the "mute" in volume control.
But I may have found something odd, I tried running audacity from the terminal, and it gives a bunch of errors, here are they:
```
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1666
Expression 'AlsaOpen( &alsaApi->baseHostApiRep, params, streamDir, &self->pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1826
Expression 'PaAlsaStreamComponent_Initialize( &self->capture, alsaApi, inParams, StreamDirection_In, NULL != callback )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2088
Expression 'PaAlsaStream_Initialize( stream, alsaHostApi, inputParameters, outputParameters, sampleRate, framesPerBuffer, callback, streamFlags, userData )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2760
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4537
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4537
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4537
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4537
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4537

```.

Also, I tried rebooting, but nothing changes.

Please help me, thanks a lot.
perfwill

---

