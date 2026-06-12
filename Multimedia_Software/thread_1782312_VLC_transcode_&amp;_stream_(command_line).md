---
title: "VLC transcode &amp; stream (command line)"
date: 2011-06-14
forum: Multimedia Software
---

### Post by macey on 2011-06-14
Can anyone please tell me why this works:-

vlc -vvv ~/Music/my_test_file.mp3 --sout '#transcode{acodec=mp3,ab=128,channels=2,samplerate=44100}:std{access=mmsh,mux=asfh,dst=:8080}'

But this doesn't:-

vlc -vvv ~/Music/my_test_file.mp3 --sout '#transcode{acodec=vorb,ab=128,channels=2,samplerate=44100}:std{access=mmsh,mux=ogg,dst=:8080}'

I  can stream the MP3 file as an mp3 stream muxed using asfh but not as a vorbis/ogg stream.

I want to stream using ogg.
The first format works fine, so I want to change as little as possible, just the transcode.
Help much appreciated.

---

