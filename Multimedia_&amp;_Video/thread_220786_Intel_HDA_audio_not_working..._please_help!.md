---
title: "Intel HDA audio not working... please help!"
date: 2006-07-22
forum: Multimedia &amp; Video
---

### Post by paolottibus on 2006-07-22
Hello I am in dispair!
I have an Acer 9800 with Intel HDA
Alsa mixer works!
Alsaconf gets my audio card well!
Still no audio...

Trying to play a file in Totem gives me:
ALSA lib confmisc.c:1105snd_func_refer) Unable to find definition 'defaults.pcm.ipc_key'
ALSA lib conf.c:3479_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3947snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2146snd_pcm_open_noupdate) Unknown PCM dmix:Intel
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4l2src'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsrc'
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open resource for writing. [gstalsasink.c(833): gst_alsasink_open (): /pipeline0/alsasink1:
Playback open error: No such file or directory]


CAN YOU HELP? PLEASE
Edit/Delete Message

---

