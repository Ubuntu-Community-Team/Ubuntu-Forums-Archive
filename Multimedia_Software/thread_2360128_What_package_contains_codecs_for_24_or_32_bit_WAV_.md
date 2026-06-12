---
title: "What package contains codecs for 24 or 32 bit WAV files?"
date: 2017-05-02
forum: Multimedia Software
---

### Post by dmitriano on 2017-05-02
Hello!

I wrote a [small test program in QT]("https://github.com/dmitriano/SoundTest") that decodes WAV and MP3 sound files with some QT API, that uses **gstreamer** internally. Looks like, to play mp3 files I need **gstreamer0.10-fluendo-mp3** package, but I am not sure what package I need to install to play WAV files with Sample Encoding 24 or 32 bit?

For example, the test program does not play a sound file with the following parameters:

Input File     : 'beep.wav'
Channels       : 2
Sample Rate    : 44100
Precision      : 24-bit
Duration       : 00:00:00.24 = 10469 samples = 17.8044 CDDA sectors
File Size      : 66.3k
Bit Rate       : 2.23M
Sample Encoding: 24-bit Signed Integer PCM

---

### Post by mc4man on 2017-05-02
I would think gstreamer does wav thru the good plugins > wavparse element (which is default installed on all Ubuntu releases
No issue here on 24 bit wav - Ex.

> $ gst-launch-1.0 filesrc location=Music/HisokanaMizugame_88_2kHz24bit.wav  ! wavparse ! alsasink
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
Redistribute latency...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstAudioSinkClock
Got EOS from element "pipeline0".
Execution ended after 0:00:46.001778725
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
Freeing pipeline ...


---

### Post by dmitriano on 2017-05-03
Your example works fine on my testing machine, but QAudioDecoder (QT class) still does not. Probably it is something related to QT. And the same situation on CentOS.

---

