---
title: "Capturing audio from DVD"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by Cod on 2008-01-14
Hi folks,
Is there a way to capture the sound from a film playing on a DVD as an mp3 or ogg file?  I want to grab some samples etc.

I realise that there are methods for capturing the sounds from the computer sounds card using audacity etc.  I just wondered if there was a way to do this more directly.

Thanks

---

### Post by vanadium on 2008-01-14
Quality wise, your best option is to rip the DVD (can be done with "vobcopy -l"), open the resulting VOB('s) and demux the audio stream. This can be done with Avidemux. This will yield an ac3 audio file, that can be converted to another audio format using for example sox, or gstreamer. Already in Avidemux, you could delete anything else than the samples you want to keep and export the audio. Alternatively, you'd demux the entire audio stream (can probably even be converted to WAV from directly from within Avidemux) and open it in Audacity for exporting the samples from there. Quality is maximally preserved because you are just converting digital data.

If quality is not the prime issue, just playing back in your media software and recording in Audacity will probably be the quickest option.

---

### Post by eye208 on 2008-01-14
VLC can play the DVD and save the audio stream, e.g. in WAV format.

---

### Post by Cod on 2008-01-14
Thanks for the suggestions people.

Quality is an issue so I'll leave the Audacity record option till last.  I'll have a look at VLC and, failing that, ripping the whole DVD and demuxing.

Cheers

---

