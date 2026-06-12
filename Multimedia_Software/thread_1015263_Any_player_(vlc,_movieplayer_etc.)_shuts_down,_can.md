---
title: "Any player (vlc, movieplayer etc.) shuts down, can`t play"
date: 2008-12-18
forum: Multimedia Software
---

### Post by Lakeside5 on 2008-12-18
After following some great advice and doing a lot of work, I finally had sound and video on my Hardy Heron server ltd os, (after 3 weeks of not) but suddenly after installing some updates on Firefox and Hardy Heron, something very annoying is happening. Despite following some advice here and other places, I can`t seem to fix this. When I click on anything (mp3 or movie) and try to play it in anything (VLC, rhythmbox, movieplayer etc.) the player pops up for one second, then closes. Whatever I try to play just shuts it down, it`s gone! Please please someone help, I was all set to view some tutorial videos to learn web design. thanks very much.

---

### Post by xc3RnbFO8P on 2008-12-18
In Terminal:
> vlc
and play something,
should give some error messages, post them here.

---

### Post by Lakeside5 on 2008-12-18
Thanks very much Ringi, this is what I got when I did as you suggested:
VLC media player 0.8.6e Janus
mdb:389, lastbuf:0 skiping granule 0
mdb:389, lastbuf:0 skiping granule 0
mdb:392, lastbuf:0 skiping granule 0
mdb:392, lastbuf:0 skiping granule 0
[00000388] pulse audio output error: Failed to connect to server: Invalid argument
[00000388] pulse audio output error: Pulse initialization failed
*** PULSEAUDIO: Unable to create stream.
*** PULSEAUDIO: Unable to create stream.
[00000388] alsa audio output error: unable to commit hardware configuration (Input/output error)
vlc: pcm_pulse.c:115: pulse_stop: Assertion `pcm->stream' failed.
Aborted
Mean anything to you?

---

### Post by xc3RnbFO8P on 2008-12-18
Try restarting pulseaudio:

In a terminal:
sudo killall pulseaudio

then hit Alt+F2, and type:
pulseaudio

---

### Post by Lakeside5 on 2008-12-18
Ok, I tried that just now, I tried all options (run in terminal, run with file-browsed to the movie, and just `run` at bottom of box). None would play the movie, and player either wouldn`t show up, or would close ;(
Also, if I click on the `sound` icon on task bar, I get: No volume control GStreamer plugins and/or devices found.

---

