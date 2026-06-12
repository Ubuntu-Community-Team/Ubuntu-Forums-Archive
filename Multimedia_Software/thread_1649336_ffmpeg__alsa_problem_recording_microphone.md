---
title: "ffmpeg / alsa problem recording microphone"
date: 2010-12-20
forum: Multimedia Software
---

### Post by aschlosberg on 2010-12-20
I am attempting to record my microphone input using ffmpeg / alsa but always receive the following error:

> 
ffmpeg -f alsa -i hw:0,0 -acodec mp3 -f video4linux2 -s 320x240 -i /dev/video0 file.mpg

[alsa @ 0xSOMEHEX]cannot set channel count to 1 (Invalid argument)


Note that the SOMEHEX is different each time.

Using arecord works perfectly with hw:0,0.

I had also tried to use /dev/snd/hwC0D0 as input but I receive an error from alsa saying that it doesn't exist (despite it existing and having adequate permissions).

I know absolutely nothing about hardware but am comfortable around the command line as I do a lot of server admin work so please be patient with my lack of knowledge :)

---

### Post by BicyclerBoy on 2010-12-20
off top off my head

add channel number
 -ac 2    or -ac 1

add sample rate ?
-ar 44100

 to you cmdline options.

move the video before the audio
do you need the stream map command ?
-map 0:0 -map 1:0    (with the video input listed first)

---

### Post by aschlosberg on 2010-12-20
Thanks BicyclerBoy!

I just added the -ac 2 option and it cleared the problem.

However the audio is not in sync with the video (it lags slightly). I am getting a warning from alsa which may be useful:

> Estimating duration from bitrace, this may be inaccurate

---

