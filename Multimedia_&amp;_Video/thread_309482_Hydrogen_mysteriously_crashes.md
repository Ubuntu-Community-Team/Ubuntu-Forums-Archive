---
title: "Hydrogen mysteriously crashes"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by k1001001 on 2006-11-29
Hello all. I've had Hydrogen on my computer for about a week, and it worked just this past weekend, but mysteriously today it decided it longer wanted to work on my computer. It will start up, and just about as it is done loading,  it disappear from the screen, and a few seconds later disappear from the taskbar. It does this whether or not the JACK server is open, so JACK is not the problem here.

Here's what I've done so far:
-Uninstalled and reinstalled Hydrogen using Add/Remove (did not download anything when reinstalled)
-Uninstalled using Add/Remove, restarting the computer, then reinstalled using Add/Remove (did not download anything when reinstalled)
-Attempted to open a song by using Nautilus to go to the tutorial song directory, /usr/share/hydrogen/data/demo_songs (crashed just before loading)
-Attempted to use Terminal to open Hydrogen (crashed)
-Attempted to use aptitude to purge, clean, autoclean, and reinstall Hydrogen (downloaded, but then did the same crash thing)

Here's the output when I open Hydrogen through Terminal (-V is the verbose logging mode):
```

keith@keith-laptop:~$ hydrogen -V
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Warning: no locale found: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8

Hydrogen 0.9.2 [Apr  8 2006]  [http://www.hydrogen-music.org]
Copyright 2002-2005 Alessandro Cominu


Compiled modules:  (FLAC) (Jack) (Alsa) (OSS) (LRDF)
Verbose log mode = active

Hydrogen comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details

Using data path: /usr/share/hydrogen/data
[INFO]      Preferences         INIT
[INFO]      Preferences         [loadPreferences] Loading preferences file (GLOBAL) [/usr/share/hydrogen/data/hydrogen.default.conf]
[INFO]      Preferences         [loadPreferences] Loading preferences file (USER) [/home/keith/.hydrogen/hydrogen.conf]
[INFO]      SongReader          [readSong] /usr/share/hydrogen/data/demo_songs/GM_kit_Diddley.h2song
[WARNING]   SongReader          [readSong] Trying to load a song created with a different version of hydrogen.
[WARNING]   SongReader          [readSong] Song [/usr/share/hydrogen/data/demo_songs/GM_kit_Diddley.h2song] saved with version 0.9.0
[INFO]      Song                INIT "Diddley"
[LadspaFX::getPluginList] reading directory: /usr/lib/ladspa
[LadspaFX::getPluginList] reading directory: /usr/local/lib/ladspa
[LadspaFX::getPluginList] directory /usr/local/lib/ladspa not found
[LadspaFX::getLadspaFXGroup]
[LadspaFX::getPluginList] reading directory: /usr/lib/ladspa
[LadspaFX::getPluginList] reading directory: /usr/local/lib/ladspa
[LadspaFX::getPluginList] directory /usr/local/lib/ladspa not found
[INFO]      Hydrogen            *** Hydrogen audio engine init ***
[INFO]      Hydrogen            [audioEngine_startAudioDrivers]
[INFO]      Hydrogen            [createDriver] Jack
[INFO]      JackDriver          INIT
[INFO]      JackDriver          Jack SampleRate changed: the sample rate is now 44100/sec
[INFO]      AlsaMidiDriver      INIT
[INFO]      JackDriver          [connect]
[INFO]      AlsaMidiDriver      alsaMidiDriver_thread() starting
[INFO]      AlsaMidiDriver      MIDI port name: None
[INFO]      AlsaMidiDriver      MIDI addr client: -1
[INFO]      AlsaMidiDriver      MIDI addr port: -1
[INFO]      AlsaMidiDriver      Midi input port at 129:0
[INFO]      AlsaMidiDriver      MIDI Thread INIT
[INFO]      Hydrogen            [audioEngine_process] Buffer size changed. Old size = 0, new size = 512
[ERROR]     Hydrogen            [audioEngine_process] Ladspa FX buffersize != nframes. FXBuffersize = 0
[INFO]      Hydrogen            [audioEngine_setupLadspaFX] buffersize=512
[INFO]      Hydrogen            [audioEngine_setupLadspaFX] m_pSong=NULL
[INFO]      Hydrogen            [audioEngine_setSong] Diddley
[INFO]      Hydrogen            [audioEngine_clearNoteQueue()]
[INFO]      Hydrogen            [audioEngine_setupLadspaFX] buffersize=512
[WARNING]   JackDriver          [setBpm] 120
[INFO]      PatEditPanel        [selectedPatternChangedEvent]
[INFO]      DrumkitManager      INIT
[INFO]      DrumkitManager      [updateDrumkitList]
[INFO]      LayerPreview        INIT
[INFO]      WaveDisplay         INIT
[INFO]      HydrogenApp         [showInfoSplash] Selected news: news-050718.htmlterminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted

```

Any suggestions at all? I'm just confused as to why it worked last week, but now will not work at all.

---

### Post by k1001001 on 2006-11-30
UPDATE: Somehow, disconnecting the computer from the internet lets Hydrogen start up without crashing. After starting up though, I can reconnect the computer and Hydrogen works just fine. Very weird.

---

### Post by Deus42 on 2006-12-07
wow, this worked for me too (Ubuntu 6.10 AMD64) when I was getting an unknown exception.

Thanks!

Error:
Mutex destroy failure: Device or resource busy
Unknown exception..

---

### Post by sam81 on 2008-01-28
Same here on Ubuntu Gutsy...

---

