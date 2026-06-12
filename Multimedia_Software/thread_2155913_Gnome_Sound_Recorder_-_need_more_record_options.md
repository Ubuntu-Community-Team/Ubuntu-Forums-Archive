---
title: "Gnome Sound Recorder - need more record options"
date: 2013-06-19
forum: Multimedia Software
---

### Post by PaulyWally on 2013-06-19
I'm using 'Gnome Sound Recorder' and 'Audio-Recorder' to perform some specific audio recording needs I have.  It would be great if I could record to 44KHz WAV, but these programs only have 22KHz WAV in their default recording presets (it appears they are getting their recording presets from the same place).

Does anyone know how to add 44KHz WAV preset?  Or any other presets for that matter?

Thanks in advance!

---

### Post by Yellow Pasque on 2013-06-20
```
sudo apt-get install gnome-media-profiles
gnome-audio-profiles-properties
```

---

### Post by osmoma on 2013-08-12
Hello,
Add your own media profile to "[media-profiles.c]("http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/media-profiles.c")" and recompile audio-recorder from source.

The actual definions in the source: [http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/media-profiles.c](http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/media-profiles.c)

Read the INSTALL file to install dependencies before make & compilation & sudo make install.

We could make both the 22 and [COLOR=#000000]44KHz WAV options permanent. What do you think?  
Like this:
[/COLOR]{"voicelossless22K","Lossless 22Khz",  "wav", "audio/x-raw,rate=22050,channels=1 ! wavenc name=enc"},
{"voicelossless44k","Lossless 44Khz",  "wav", "audio/x-raw,rate=[COLOR=#000000]44100[/COLOR],channels=1 ! wavenc name=enc"},
[COLOR=#000000]
Test the pipeline in a terminal window (play some music/sound and record it to file1.wav):
[/COLOR]
```
gst-launch-1.0 -e pulsesrc ! audioconvert ! 'audio/x-raw,rate=44100,channels=1' ! queue ! wavenc ! filesink location=file1.wav
```[COLOR=#000000]
[/COLOR]$ file file1.wav [COLOR=#000000]
[/COLOR]$ totem file1.wav 
[COLOR=#000000]
(Send me your comments/changes and/or patch)

[/COLOR][COLOR=#ff0000]EDIT: [/COLOR][COLOR=#000000]A better idea;  Maybe we could add bit-rate and other audio options to the [Settings].

Audio-recorder: [/COLOR][https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

---

