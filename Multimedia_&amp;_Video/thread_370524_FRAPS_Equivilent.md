---
title: "FRAPS Equivilent"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by Dylnuge on 2007-02-25
Hello,

Does anyone know of a Linux equivalent to FRAPS (screen recorder).

Thanks
-Dylan

---

### Post by Ademan on 2007-07-08
I know i'm sort of resurrecting the thread, but I found myself looking for the same thing just today.

cheers
-Dan

---

### Post by AnRa on 2007-07-08
Istanbul

---

### Post by Drunky on 2007-07-09
[http://recordmydesktop.sourceforge.net/](http://recordmydesktop.sourceforge.net/)

I saw an article about Recordmydesktop.  Don't know much about it though.

---

### Post by Delvien on 2007-07-15
Neither of these work properly when recording a 3d game, ( World of warcraft ) The recording is chunky, and has 3d blocks everyhwere.

---

### Post by acoustibop on 2007-07-15
You could try gvidcap or xvidcap - the latter has more recent versions, but won't work with 3D acceleration.  Works better than anything else I've tried.

---

### Post by MarilenCorciovei on 2007-07-18
[Here is an short explanation]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/screencasts-with-xvidcap") on how to use xvidcap on ubuntu linux to create and publish your screencast on the web.

---

### Post by alterpinguin on 2007-07-19
this is one long cmdline-entry:
gst-launch oggmux name=mux ! filesink location=demorec.ogg ximagesrc startx=10 starty=20 endx=330 endy=260 use-damage=false ! video/x-raw-rgb,framerate=10/1 ! ffmpegcolorspace ! theoraenc quality=40 ! queue ! mux. alsasrc ! audio/x-raw-int,channels=2 ! audioconvert ! vorbisenc ! queue ! mux.


used with ubuntu 7.04, default gstreamer install the gstreamer-0.10.12

what does this line?

first, gstreamer uses "!" as a kind of pipe-symbol to build up its parts.

so gst-launch starts up  the creation of an ogg-file stored under the name: demorec.ogg.
Then there are the parts used as source for this ogg,
  first its the video-part: ximagesrc with some settings about size
                then the framerate, only 10/1 fps, -- ! check your computer performance
                with encoding to the theora-codec
 second the audio-part, it uses the default alsasrc - read arecord man-page of alsa for more hints
how to setup a copy-device and you may use this, or specify the micro-channel
              the audio is encoded with the vorbis code

to instpect other options of, for example: ximagesrc
enter: gst-inspect ximagesrc

if you have installed istanbul with its better istximagesrc, you should use this
-- and there are options to record uncompressed (spare the encoding-cpu-usage) as gdpay format files
and reading those later and encoding. But all does not help if the computer power is to weak and you try to record too big parts - remember twice the video-size does not double the cpu-usage, ! it goes up by factor 4.
Only if you double the fps-rates, you will need twice the cpu-usage.

you NEED to disable xdamge usage and always record the screen if you want to record programs (like 3d-games) which write directly to their screen-area.

---

### Post by roguenoir on 2007-08-29
I used Istanbul to record videos in World of Warcraft but for some reason, the recording is very choppy unless I record in windowed mode.  (I routinely get 100+ fps in the game, maybe half that while recording.)

I'm using Cedega in D3D mode btw.

[URL="http://video.google.com/videoplay?docid=4733545322628453528&q=twinkhunter&total=1&start=0&num=10&so=0&type=search&plindex=0"]
Here's an example of my video recorded in Ubuntu using Istanbul[/URL]

---

### Post by Rhubarb on 2007-08-30
To capture openGL you should be using yukon and seom.
It does not capture sound.
[http://www.neopsis.com/projects/yukon/](http://www.neopsis.com/projects/yukon/)

I couldn't figure out how to get yukon and seom running, so I got a friend to help me out (sorry I can't help you to get it going on your pc)

Once captured you'll need to encode the video, I use mencoder to do this:
```
seom-filter ~/file | mencoder - -o output.avi -vf eq2=1.4 -ovc x264 -x264encopts threads=3:bitrate=1500 -oac pcm
```

There's a nice youtube video of this:
[http://www.youtube.com/watch?v=d_fP6yYg5M8](http://www.youtube.com/watch?v=d_fP6yYg5M8)

Some people have had problems getting it to work with wine apps:
[http://www.winehq.org/pipermail/wine-bugs/2007-May/056121.html](http://www.winehq.org/pipermail/wine-bugs/2007-May/056121.html)

I use yukon + seom to capture openGL games, mostly [http://www.sauerbraten.org/](http://www.sauerbraten.org/)

Hope this of help to you.

---

