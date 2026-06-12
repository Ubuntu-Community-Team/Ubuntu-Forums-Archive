---
title: "Soundblaster Live! Platinum"
date: 2005-12-08
forum: Multimedia &amp; Video
---

### Post by Doughsay on 2005-12-08
Hello,

I'm trying to get my soundblaster live working properly in Ubuntu Breezy 5.10.  Sound currently works fine, except whn running audio production tools such as Audacity and Hydrogen.  The sound lags behind and in Hydrogen the interface freezes every few milliseconds.

Running Hydrogen in the console produces this output, the bottom lines repeat every few milliseconds:
```

Hydrogen 0.9.2-beta3 [Aug 10 2005]  [http://www.hydrogen-music.org]
Copyright 2002-2005 Alessandro Cominu

Compiled modules:  (FLAC) (Jack) (Alsa) (OSS) (LRDF)

Hydrogen comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details

Using data path: /usr/share/hydrogen/data
Warning: no locale found: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8
[WARNING]   SongReader          [readSong] Trying to load a song created with a different version of hydrogen.
[WARNING]   SongReader          [readSong] Song [/usr/share/hydrogen/data/demo_songs/tutorial_georgyporgy.h2song] saved with version 0.9.0
[LadspaFX::getPluginList] reading directory: /usr/lib/ladspa
[LadspaFX::getPluginList] directory /usr/lib/ladspa not found
[LadspaFX::getLadspaFXGroup]
[LadspaFX::getPluginList] reading directory: /usr/lib/ladspa
[LadspaFX::getPluginList] directory /usr/lib/ladspa not found
[WARNING]   JackDriver          Jack server not running?
[ERROR]     Hydrogen            [audioEngine_startAudioDrivers] Error starting audio driver [audioDriver::init()]
[WARNING]   Hydrogen            [audioEngine_setupLadspaFX] m_pSong=NULL
[ERROR]     AlsaAudioDriver     Can't set realtime scheduling for ALSA Driver
[WARNING]   Hydrogen            [audioEngine_process_checkBPMChanged] fNewFrames nan, m_transport.m_nFrames: 0
[WARNING]   Hydrogen            [audioEngine_seek()] seek in 0 (old pos = 0)
[ERROR]     AlsaAudioDriver     [alsaAudioDriver_processCaller] XRUN
[ERROR]     AlsaAudioDriver     [alsaAudioDriver_processCaller] XRUN
[ERROR]     AlsaAudioDriver     [alsaAudioDriver_processCaller] XRUN
[ERROR]     AlsaAudioDriver     [alsaAudioDriver_processCaller] XRUN
[ERROR]     AlsaAudioDriver     [alsaAudioDriver_processCaller] XRUN
...etc

```

I haven't messed with any alsa drivers or anything relating to sound yet.  I want to know what steps I can take for the audio to work flawlessly in audio production software, and just in general.

I just get this feeling that Ubuntu sets stuff up with default settings and drivers, which work ok for most things, but I'd like to get it all working properly.  Hydrogen is the main problem right now.

---

