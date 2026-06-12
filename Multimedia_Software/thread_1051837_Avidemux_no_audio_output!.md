---
title: "Avidemux no audio output?!"
date: 2009-01-27
forum: Multimedia Software
---

### Post by MIH1406 on 2009-01-27
Hello,

Avidemux cannot output the audio and shows this message:

"Trouble initializing audio device"

I have checked 'Edit'->'Preferences.'->'Audio'

And here is the selections:
Local playback downmixing: Pro Logic
Volume control: Master
Audio output: ALSA
ALSA device: dmix


What is the ALSA device and how can I check my ALSA device

---

### Post by vanadium on 2009-01-27
It will if you shut down other applications that use audio. However, can you try "Pulse Audio" for Audio output? Volume control is set to "PCM" for me, but that probably won't make the difference. In "Sound Preferences" I have it all set to Pulse Audio Server". (Pulse Audio is Ubuntu Hardy and above).

---

### Post by MIH1406 on 2009-01-28
Not worked yet I tried all the options but I couldn't successful with any.

Is it right that the alsa device in my laptop is dmix???

How can I check that?

---

### Post by vanadium on 2009-01-28
For me it is also dmix, and the selection is grayed out. Other settings in the Avidemux dialog are (in sequence) "Pro logic", "PCM", "Pulse Audio". In Preferences - Sounds, I have "Pulse Audio" thoughout, except for the last selection, which is "Intel ICH6 (Alsa mixer" for me, but these settings will depend on your sound card.

---

### Post by Evengard on 2009-12-10
The only way I found to run it is to use padsp and setting driver to OSS...

---

