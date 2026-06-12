---
title: "Espeak to Airport Express"
date: 2009-03-05
forum: Multimedia Software
---

### Post by jobless on 2009-03-05
I am trying to stream the audio output from espeak to an apple airport express. Here are the steps I followed.

espeak -v en "This is a test" -w test.wav
lame test.wav test.mp3
lame --decode test.mp3 - | JustePort.exe - 10.0.0.2 0
(JustePort.exe was built using the guide at [http://ubuntuforums.org/showthread.php?t=192806](http://ubuntuforums.org/showthread.php?t=192806))

I don't hear anything from the speakers attached to the airport express. So I tried a longer file and all I got was super fast audio (or maybe just corrupt audio) from the speakers.

Playing a normal mp3 file (copied over from windows), using the following approach works fine. Following is the file info for the windows mp3 file and the converted mp3 file from lame.

lame.mp3 - MPEG ADTS, layer III, v2,  32 kBits, 22.05 kHz, Monaural
windows.mp3 - Audio file with ID3 version 24.0 tag, MP3 encoding

Has anybody observed this behavior before? I tried not adding any lame tags to mp3 files, I tried just piping the wav file from espeak too. I even downloaded ffmpeg and converted to mp3 using it, with no luck on playback to airport express.

Thanks for any help.

---

