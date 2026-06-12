---
title: "VLC - no sound during video  capture"
date: 2012-04-25
forum: Multimedia Software
---

### Post by baby_panda on 2012-04-25
Hi I tried to use VLC player to record a video. But it is not recording sound. I can't hear any sound during video capture or playback of the recorded file. I used the "Open Capture Device" option in Media menu. Capture mode was Video 4 Linux 2. For the audio device name, I tried many options:
1) alsa://
2) alsa://hw:0,0
3) alsa://plughw
4) alsa://plughw:Intel
Vlc did not display any error during capture. But still I could not hear any sound. Please, can somebody help me? (I have Ubuntu 11.10 with built-in web-cam in my laptop. In System settings, my built-in microphone is not muted.)

---

### Post by ullix on 2012-05-12
wish I could help, but can only second to the effect:

using a video grabber (Terratec Grabster AV350MX) connected via USB I can play and record video AND sound just fine with mplayer/mencoder, but using vlc from gui or command line with many variations on alsa gives good picture, but no sound whatsoever.

arecord -l shows my sound input on card1, dev 0.

I guess it is a bug in vlc, but I also find no bug reports.

---

### Post by ginjabunny on 2012-05-13
have a look on [http://wiki.videolan.org/](http://wiki.videolan.org/), I found some really useful command line examples when I was looking to record internet radio streams, it talks about transcoding and duplicating streams, I end up with stuff that works (and is not as complicated as it looks), for example

DISPLAY=:0.0 timeout 1800 vlc --quiet --no-video --no-qt-error-dialogs --live-caching 4000 --sout-keep --sout-file-append --sout "#duplicate{dst=display,dst='transcode{aenc=ffmpeg,acodec=mp3,ab=128,channels=2,samplerate=44100}:duplicate{dst=std{access=file,mux=dummy,dst=PROGFILE.mp3},dst=std{access=http,mux=dummy,dst=192.168.1.1:8080}}'}" PLAYLIST.pls

this will start VLC with the radio stream in PLAYLIST.pls and forwards it on which I can then pick up around he house on other PCs and my wireless speaker in the bathroom, and it records the stream to PROGFILE.mp3 and quits after 30 mins.

You answer is probably on the VLC site somewhere.

---

