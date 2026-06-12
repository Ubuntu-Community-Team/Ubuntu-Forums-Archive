---
title: "How to convert particular audio format"
date: 2008-05-11
forum: Multimedia Software
---

### Post by kk0sse54 on 2008-05-11
Was downloading some audio files today from this site and when I went to open them they were in .ra format or in other words RealAudio format. I've have never come across this format before and the only program that I can open it with is Mplayer. What I need is to be able to convert the files into mp3 so that I can put them on my ipod but so far all the converting programs I have don't recognize the files. Does anybody know of any program to convert them or some codec so that I can at least play them in my normal music player?
Edit: I just realized this but are these files meant to be played in RealPlayer? So if I boot into windows and play them in Realplayer can I convert them there?

---

### Post by kk0sse54 on 2008-05-15
Anybody? Opinions facts concerns something?

---

### Post by linuxfan3 on 2008-05-15
when i googled i only found some suitable converters for windows. maybe you try them under wine...

---

### Post by kk0sse54 on 2008-05-15
Thanks for responding :). I was thinking of booting into windows and doing the conversion from there instead of dealing with wine but it would be really nice in the future if I could get something native for linux that would do it for me.

---

### Post by Goodbytes on 2008-07-08
What I've ended up doing for now is to use mplayer to read the realaudio file in and spit it out to disk as a .wav file:

mplayer -ao pcm:waveheader:file=desired_filename.wav realaudiofile.ra

On my machine it converts an hour's worth of realaudio to .wav in 12 seconds, even without using the "fast" option. :D

---

