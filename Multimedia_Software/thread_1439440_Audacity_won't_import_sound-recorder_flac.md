---
title: "Audacity won't import sound-recorder flac"
date: 2010-03-26
forum: Multimedia Software
---

### Post by thundre on 2010-03-26
Background:  I'm digitizing an old record.  I used Sound Recorder to make FLACs of each side of the LP, and now I need to edit them down to individual tracks.  I'm using the development version of Ubuntu 10.04.

Problem:  Audacity ignores these FLAC files when I attempt to import or open them.

The FLAC files play if I hover the mouse over them in GNOME.  

Audacity gladly imports FLAC files I ripped from CD last year (using Sound Juicer I think).

But when I try to do the same for my recorded FLAC files, nothing happens.  I tried running audacity in a terminal window, and there is no additional output when I attempt the import.  This comes out when I start it:
```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3653

```Looking at the file properties, they're basically the same except the Juicer-generated file has values filled in for title, artist, album, year.  They are all FLAC Stereo 44100 Hz.  I thought it might be a file-size problem, so I made a 5-second test with Sound Recorder, and that also refuses to import.

So, why do only the ripped files work with Audacity?

---

### Post by thundre on 2010-03-29
I have successfully worked around the problem using "flac -d" to convert the Sound Recorder .flac files into .wav files.  The compression was not all that great anyway, about 8:5.

My conclusion from this is that Audacity's flac import probably expects something that Sound Recorder does not provide, and that Sound Recorder's flac encoding is inefficient.  So use wav with Sound Recorder.

---

### Post by jkk10 on 2010-04-14
Thanks with the Q & A. It helped me!

---

### Post by ethanay on 2010-09-17
thanks also, this workaround helped me!

---

### Post by am529 on 2010-12-27
You can also just use SoundConverter (can be found in Synaptic or Software Center) to convert the file to FLAC. There will be no apparent change to the audio file (that I can tell), but Audacity will be able to import it afterwards.

---

### Post by tonyshangrila on 2011-03-09
> **am529 said:**
> You can also just use SoundConverter (can be found in Synaptic or Software Center) to convert the file to FLAC. There will be no apparent change to the audio file (that I can tell), but Audacity will be able to import it afterwards.

Strange, but true.  This worked for me, too.  "Converted" version was same sample rate, length, very slightly smaller.  *shrug*

---

