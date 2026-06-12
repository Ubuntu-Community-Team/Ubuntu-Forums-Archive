---
title: "Screen recording software won't capture ALSA audio"
date: 2015-05-14
forum: Multimedia Software
---

### Post by Zeikcied on 2015-05-14
I'm trying to record video and audio from Mednafen, a multi-system emulator.  I've tried RecordMyDesktop, Kazam, SimpleScreenRecorder, and Vokoscreen.  I'm able to get each of them to record the video just fine, but none will capture the audio.

Mednafen defaults to ALSA for its audio output, and Kazam, SimpleScreenRecorder, and Vokoscreen allow selecting ALSA as the audio stream to capture, but none grab the Mednafen audio.  I tested a couple of them with a YouTube video (played via the HTML5 player in Firefox) and they capture that audio just fine.  It's just Mednafen that they won't record.

I have no idea what to do.  The game I'm playing is a PSOne game, and I haven't had any luck with any other PSX emulators native on Linux.  Mednafen has been the best performing one so far.  Which is unfortunate, given that I can't seem to get audio to record from it.

Is there anyone who knows of a way to fix this?

EDIT: I tried using SimpleScreenRecorder to record VLC (which is set to output using ALSA) and it didn't capture that audio, either.  So I'm assuming it's an issue with capturing ALSA audio in general.  I've tried all the available ALSA devices, and it doesn't record sound from any of them.  Am I missing something?  Can this be fixed somehow?

Oh, I'm running Kubuntu 15.04, if that makes any difference.

---

### Post by dino99 on 2015-05-14
have you tried streamripper from the archive ?

---

### Post by Zeikcied on 2015-05-14
> **dino99 said:**
> have you tried streamripper from the archive ?

That seems to be just for audio. I want to capture both the video and the audio.  I can get the video just fine, but ALSA audio isn't recording in any of the tested desktop recording software.

---

