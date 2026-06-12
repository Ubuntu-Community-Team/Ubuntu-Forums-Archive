---
title: "dvd-slideshow issues"
date: 2009-02-02
forum: Multimedia Software
---

### Post by deadmnky on 2009-02-02
so i am trying to learn dvd-slideshow cli version after trying to use man-dvd and qtdvdauthor with no luck. i can get a script done and start the dvd process but end up getting two errors i think. this is just a test version as i am learning but was hoping someone had some answers to this error output.
the error is as follows


```
 ###########################################################
[dvd-slideshow] Found 0 images.
[dvd-slideshow] Found 0 audio files.
[dvd-slideshow] Found 3 background slides.
[dvd-slideshow] Found 1 title slides.
[dvd-slideshow] Found 4 transitions (fadein/fadeout/crossfade/wipe).
[dvd-slideshow] Video: NTSC 720x480 29.97fps 4:3
[dvd-slideshow] Audio: AC3 48000 192
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=dvd Border=0
[dvd-slideshow] Using SMP optimizations for multi-processor machines
[dvd-slideshow] Title_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Subtitle_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Total audio length = 
[dvd-slideshow] Total video length = 0:0:45.000
[dvd-slideshow] Output filename is tester_run
[dvd-slideshow] Temp dir is /home/deadmnky/dvd-slideshow_temp_15261
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] background 0:0:1.000
[dvd-slideshow] Displaying background black
[dvd-slideshow]############################################################
[dvd-slideshow] Applying Fadein to next image 0:0:1.000
[dvd-slideshow]###########################################################xargs: cat: terminated by signal 13

[dvd-slideshow] Title 0:0:5.000
[dvd-slideshow]         Title=tester
[dvd-slideshow]############################################################
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Doing fadeOUT to background....
[dvd-slideshow] Applying Fadeout to previous image 0:0:1.000
[dvd-slideshow]###########################################################xargs: cat: terminated by signal 13

[dvd-slideshow] background 0:0:2.000
[dvd-slideshow] Displaying background black
[dvd-slideshow]############################################################
[dvd-slideshow] Applying Fadein to next image 0:0:1.000
[dvd-slideshow] ERROR: Cannot fadein to another fade!
[dvd-slideshow] cleanup...
/usr/bin/dvd-slideshow: line 913: kill: (17466) - No such process

```

here ismy dir2dvdslideshow script

```
background:0::black
background:1
fadein:1
title:5:tester
background:0::black
fadeout:1
background:2
fadein:1
/home/deadmnky/Pictures/wierd flix/wierd:5
/home/deadmnky/Pictures/wierd flix/wierd:5
/home/deadmnky/Pictures/wierd flix/wierd:5
/home/deadmnky/Pictures/wierd flix/wierd:5
/home/deadmnky/Pictures/wierd flix/wierd:5
/home/deadmnky/Pictures/wierd flix/wierd:5
/home/deadmnky/Pictures/wierd flix/wierd:5
fadeout:1
background:2
```

its small so i can learn thank you for any help you can give. i am still unfamiliar with this program so if i am messing up somewhere thank you for your patience

---

### Post by deadmnky on 2009-02-02
so i am guessing that i am missing the extensions and there lies the problem. i tried doing it this way 

```
dir2slideshow -n 'tester' -t 5 -r /home/deadmnky/Pictures/"wierd flix"  /home/deadmnky
```

si tried this post [http://ubuntuforums.org/showthread.php?t=788085&highlight=dvd+slideshow](http://ubuntuforums.org/showthread.php?t=788085&highlight=dvd+slideshow) it seemed to get me past some issues. now i am stuck with the following in my logs

```
Unknown encoder 'mpeg2video'
```

then it finishes up the slide show and produces the following error at the end

```
video:0kB audio:10546kB global headers:0kB muxing overhead 0.000000%
[dvd-slideshow] ERROR: no output .mpg file found!
[dvd-slideshow] This usually happens when ffmpeg screws up something
[dvd-slideshow] or one image is messed up and the resulting video can't be created
[dvd-slideshow]############################################################
[dvd-slideshow] Multiplexing audio and video...
[dvd-slideshow] Some sequence marker warnings here are normal
**ERROR: [mplex] Unable to open file /home/deadmnky/dvd-slideshow_temp_7211/video.mpg for reading.
[dvd-slideshow] ERROR during mplex execution!
[dvd-slideshow] see /home/deadmnky/dvd-slideshow.log for details
[dvd-slideshow] cleanup...
```

---

