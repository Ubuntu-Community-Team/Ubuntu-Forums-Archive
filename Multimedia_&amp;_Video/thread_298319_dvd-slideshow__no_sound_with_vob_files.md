---
title: "dvd-slideshow : no sound with vob files"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by Wiki_Poster on 2006-11-12
I installed and tried to use dvd-slideshow in order to create a .vob file, everything went OK except that i don't have any sound.

$ dvd-slideshow -n 'test' -f test.txt  - a test.mp3 -p
> 
[dvd-slideshow]            dvd-slideshow 0.7.5
[dvd-slideshow]            Licensed under the GNU GPL
[dvd-slideshow]            Copyright 2003-2006 by Scott Dylewski
....
############################################################
[dvd-slideshow] Found 19 images.
[dvd-slideshow] Found 1 audio files.
[dvd-slideshow] Found 2 background slides.
[dvd-slideshow] Found 1 title slides.
[dvd-slideshow] Found 3 transitions (fadein/fadeout/crossfade).
[dvd-slideshow] Video: PAL  Audio: AC3
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=render
[dvd-slideshow] Decoding command-line passed audio files...
[dvd-slideshow] Decoding mp3 audio: test.mp3...
[dvd-slideshow] Total video length = 0:1:5.000
[dvd-slideshow] Output filename is test_rezo_1
[dvd-slideshow] Temp dir is /home/nick/temp/dvd-slideshow_temp_12045
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Title 0:0:3.000
[dvd-slideshow]         Title=Rezo 1
[dvd-slideshow]############################################################
[dvd-slideshow] Fadeout 0:0:1.000
[dvd-slideshow]############################################################
[dvd-slideshow] background 0:0:1.000
[dvd-slideshow] Displaying background image black
[dvd-slideshow]############################################################
[dvd-slideshow] Fadein 0:0:1.000
[dvd-slideshow]############################################################
[dvd-slideshow] 1/19 ...
...
[dvd-slideshow] 19/19 ...
[dvd-slideshow]############################################################
[dvd-slideshow] Fadeout 0:0:1.000
[dvd-slideshow]############################################################
[dvd-slideshow] background 0:0:1.000
[dvd-slideshow] Displaying background image black
[dvd-slideshow]############################################################
[dvd-slideshow] waiting for mpeg2enc to finish...
[dvd-slideshow]#####################################
[color=red][dvd-slideshow] Processing command-line audio...
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] ..test.mp3
[dvd-slideshow] fade_in_time=0:0:3.000 fade_out_time=0:0:3.000
[dvd-slideshow] total_audio_length=0:0:0.000
sox: Can't open input file '/home/nick/temp/dvd-slideshow_temp_12045/audio1_ 0000.wav': No such file or directory[/color]
[dvd-slideshow] ###############
[dvd-slideshow] Buffering end of audio file with silence for 0:1:6.000
[dvd-slideshow] Creating ac3 audio for test.mp3...
[dvd-slideshow]############################################################
[dvd-slideshow] Multiplexing audio and video...
[dvd-slideshow]############################################################
[dvd-slideshow] No subtitles... removing .spumux file
[dvd-slideshow] total chapters=20
[dvd-slideshow] chapter markers at 0,0:0:6.000,0:0:9.000,0:0:12.000,0:0:15.000,0 :0:18.000,0:0:21.000,0:0:24.000,0:0:27.000,0:0:30.000,0:0:33.000,0:0:36.000,0:0: 39.000,0:0:42.000,0:0:45.000,0:0:48.000,0:0:51.000,0:0:54.000,0:0:57.000,0:1:0.0 00
[dvd-slideshow]############################################################
[dvd-slideshow] cleanup...
[dvd-slideshow] More extensive logfile output is at:
[dvd-slideshow] /home/nick/temp/dvd-slideshow.log
[dvd-slideshow] Done!

As you may see in red, it looks like no wav audio file is created. As a consequence, i don't have any sound on the .vob file. I tried several times...

Do you have any idea ?

---

### Post by Wiki_Poster on 2006-11-15
Any idea now ?

---

### Post by FernandoMilton on 2007-03-03
It's a bug on dvd-slideshow dependencies. Install lame and it shall work. sudo apt-get install lame :D

---

### Post by un-tu-3-4 on 2007-12-03
I just came across this same problem... Been driving me crazy for a couple of weeks. It worked for me like a charm. Thanks!

---

