---
title: "Audacity freezes (underrun occured)"
date: 2014-12-23
forum: Multimedia Software
---

### Post by beep3 on 2014-12-23
I'm trying to edit an MP3 file using Audacity. It will open the file and I can listen to it but as soon as I touch the timeline or try to skip through the clip (for instance using the 'arrow right' key) the programme starts misbehaving. The sound changes to what it's best described as a scratched record and seconds later the programme freezes. This happens each and every time - it's not a one-off crash.

When I launch Audicity I get this output:

```
(process:8282): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised
(process:8282): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised
(process:8282): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised
(process:8282): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
ALSA lib pcm_dsnoop.c:618:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1736
Expression 'AlsaOpen( &alsaApi->baseHostApiRep, params, streamDir, &self->pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1904
Expression 'PaAlsaStreamComponent_Initialize( &self->capture, alsaApi, inParams, StreamDirection_In, NULL != callback )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2171
Expression 'PaAlsaStream_Initialize( stream, alsaHostApi, inputParameters, outputParameters, sampleRate, framesPerBuffer, callback, streamFlags, userData )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2840
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4611
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4611
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4611
```

After touching the timeline I get many hundreds of lines that say: 

```
ALSA lib pcm.c:7843:(snd_pcm_recover) underrun occurred
```

From what I read elsewhere I gather there might be something wrong with the settings, in particular the output device. I've no idea what the settings should and have randomly tried different options, to no avail. Any help would be much appreciated.

If it's helpful, I'm running Ubuntu 14.04, 64 bits.

---

### Post by beep3 on 2014-12-24
Cracked it, thanks to [this thread]("http://forum.linuxmint.com/viewtopic.php?f=48&t=174754&p=901001") on the Mint forums. For the benefit of anyone trying to solve the same bug...


[LIST]
[*]Make sure no application is using Pulseaudio. 
[*]Launch Audicity from the command line using **env PULSE_LATENCY_MSEC=30 audacity &**. 
[*]Select an option with hw from the Output device select list (in the Device toolbar). 
[/LIST]

In my case I have five items (devices?) with **hw** in the name. The first three prevented Audacity from crashing but didn't produce sound. The fourth one (*HDA Intel PCH: ALC892 Analog (hw: 1,0*) was bingo.

I've got no idea why this solved the issue and when I launch Audacity it still shows the same errors as before - only the 'underrun occurred' error is gone. If anyone understands what's happening I'd be keen to find out!

---

