---
title: "Phonon (QT) doesn't work"
date: 2010-04-13
forum: Multimedia Software
---

### Post by benskiedra on 2010-04-13
Hello everyone,

Using ubuntu 9.10 here and having some problems with Phonon library. I've written a simple test app with Qt for playing some mp3 files using Phonon.
Program compiles, runs, no errors are thrown, however, sound does not appear, too. A strange thing I've noticed when I've put a line of code that outputs the current state of the mediaObject right after calling its play() method: when using phonon-backend-gstreamer (having xine backend removed) it shows Phonon::LoadingState state, when gstreamer backend is removed and xine's used instead, it shows Phonon::ErrorState.

I have ubuntu-restricted-extras, libxine1-ffmpeg, libqt4-phonon, libqt4-phonon-dev packages installed.

When running my program with debug enabled:
```
me@laptop:/media/sandelys/_lin/sound_lin$ PHONON_GST_DEBUG=3 ./sound -qws
"PGST(2): Using GStreamer 0.10.25" 
"PGST(2): AudioOutput using gconf audio sink" 
"PGST(3): Found new audio device default  (DeviceManager 0x84842c8)" 
"PGST(2): Begin source load  (MediaObject 0x8519f30)" 
"PGST(2): AudioOutput using gconf audio sink" 
"PGST(2): virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(const Phonon::AudioOutputDevice&)  (AudioOutput 0x8537d68)" 
"PGST(2): virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(int)0  (AudioOutput 0x8537d68)" 
"PGST(2): Backend connected Phonon::Gstreamer::MediaObject to Phonon::Gstreamer::AudioOutput" 
"PGST(2): Begin source load  (MediaObject 0x8519f30)" 
"PGST(2): Begin source load  (MediaObject 0x85493f8)" 
"PGST(2): AudioOutput using gconf audio sink" 
"PGST(2): virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(const Phonon::AudioOutputDevice&)  (AudioOutput 0x85524a0)" 
"PGST(2): virtual bool Phonon::Gstreamer::AudioOutput::setOutputDevice(int)0  (AudioOutput 0x85524a0)" 
"PGST(2): Backend connected Phonon::Gstreamer::MediaObject to Phonon::Gstreamer::AudioOutput" 
"PGST(2): Begin source load  (MediaObject 0x85493f8)" 
"PGST(3): Bus: state-changed (fakesink)  (MediaObject 0x8519f30)" 
"PGST(3): Bus: state-changed (fakesink)  (MediaObject 0x85493f8)" 
"PGST(3): Bus: state-changed (typefind)  (MediaObject 0x8519f30)" 
"PGST(3): Bus: state-changed (typefind)  (MediaObject 0x85493f8)" 
"PGST(3): Bus: state-changed (decodebin0)  (MediaObject 0x8519f30)" 
"PGST(3): Bus: state-changed (decodebin1)  (MediaObject 0x85493f8)" 
"PGST(3): Bus: state-changed (pipeline0)  (MediaObject 0x8519f30)" 
"PGST(3): gstreamer: pipeline state set to ready  (MediaObject 0x8519f30)" 
"PGST(3): Bus: state-changed (pipeline1)  (MediaObject 0x85493f8)" 
"PGST(3): gstreamer: pipeline state set to ready  (MediaObject 0x85493f8)" 
"PGST(3): Bus: state-changed (typefind)  (MediaObject 0x8519f30)" 
"PGST(3): Bus: state-changed (typefind)  (MediaObject 0x85493f8)" 
"PGST(2): Begin source load  (MediaObject 0x8519f30)" 
"PGST(2): Begin source load  (MediaObject 0x8519f30)" 
"PGST(3): Bus: state-changed (fakesink)  (MediaObject 0x8519f30)" 
"PGST(3): Bus: state-changed (typefind)  (MediaObject 0x8519f30)" 
"PGST(3): Bus: state-changed (decodebin0)  (MediaObject 0x8519f30)" 
"PGST(3): Bus: state-changed (pipeline0)  (MediaObject 0x8519f30)" 
"PGST(3): gstreamer: pipeline state set to ready  (MediaObject 0x8519f30)" 
"PGST(3): Bus: state-changed (typefind)  (MediaObject 0x8519f30)"
```

And Phonon::BackendCapabilities::availableAudioOutputDevices() has only one device listed which is "default".

Any help on this issue would be really appreciated, otherwise my game won't have sound effects at all :(

---

### Post by Chronon on 2010-04-13
Do you have phonon-backend-xine and/or phonon-backend-gstreamer?

---

### Post by benskiedra on 2010-04-13
As I've said, yes. But either with one of them or both installed, situation remains the same - mp3 track does not play..

---

### Post by Chronon on 2010-04-13
Sorry about that.  It seems I didn't read closely enough.  :-|

Do other applications play audio fine using phonon?

Edit: You may get better responses in the programming/development forum.

---

