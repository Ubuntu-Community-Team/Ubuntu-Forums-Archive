---
title: "Subittles Question"
date: 2010-02-08
forum: Multimedia Software
---

### Post by timinator94 on 2010-02-08
Hi all,
I got some anime videos from a friend and they are encoded in .mkv with subtitles. I would like to convert them into .3gp and .mp4 but when i do theres no subs...... please tell me how and with what to make the subs appear... I dont want to learn japanese;)... thanks
The Timinator

---

### Post by lovinglinux on 2010-02-09
You need to extract the subtitles from the mkv files using [mkvtoolnix-gui](apt:mkvtoolnix-gui), then mux them to the mp4 files using MP4Box. I never used that method, tho. Instead, I harcode the subtitles into the mp4 video stream with mencoder:

```
mencoder source_video.avi -sub source_subtitles.ssa -a\s\s -a\s\s-color FFFF0000 &#8722;\a\s\s&#8722;font&#8722;scale 3 -o output_video.mp4 -oac lavc -lavcopts acodec=libfaac:abitrate=128 -ovc lavc -lavcopts vcodec=libx264:vbitrate=1500
```

---

### Post by VertexPusher on 2010-02-09
Encoding SSA subtitles with MEncoder doesn't work well because all the formatting (fonts, colours, alignment, positioning, rotation etc.) will be lost. Avidemux will do a better job here because it has a rendering filter for SSA subtitles.

---

### Post by lovinglinux on 2010-02-09
> **VertexPusher said:**
> Encoding SSA subtitles with MEncoder doesn't work well because all the formatting (fonts, colours, alignment, positioning, rotation etc.) will be lost. Avidemux will do a better job here because it has a rendering filter for SSA subtitles.

Not true. It works perfectly and much better than avidemux. All formatting is preserved with that command I have posted. See attached screenshot.

Perhaps it is because I use the [rmv ppa](https://launchpad.net/~rvm/+archive/mplayer).

---

### Post by VertexPusher on 2010-02-09
> **lovinglinux said:**
> Not true. It works perfectly and much better than avidemux.
OK, with a patched version anything is possible. I've been waiting for that feature to enter the official codebase, but last time I looked, it wasn't there.

---

### Post by lovinglinux on 2010-02-09
> **VertexPusher said:**
> OK, with a patched version anything is possible. I've been waiting for that feature to enter the official codebase, but last time I looked, it wasn't there.

Just use that ppa. It's from the smplayer developer.

---

### Post by qyot27 on 2010-02-10
> **lovinglinux said:**
> You need to extract the subtitles from the mkv files using [mkvtoolnix-gui](apt:mkvtoolnix-gui), then mux them to the mp4 files using MP4Box. I never used that method, tho. Instead, I harcode the subtitles into the mp4 video stream with mencoder:

```
mencoder source_video.avi -sub source_subtitles.ssa -a\s\s -a\s\s-color FFFF0000 &#8722;\a\s\s&#8722;font&#8722;scale 3 -o output_video.mp4 -oac lavc -lavcopts acodec=libfaac:abitrate=128 -ovc lavc -lavcopts vcodec=libx264:vbitrate=1500
```
Actually, you don't need to extract the subtitles, or even declare all those extra formatting parameters.  Using that SMPlayer ppa build of mencoder you mentioned (thanks for that by the way, it was driving me up a wall trying to find one similar to the Windows builds I was working with), all I needed to do was use -*a**s**s* and -fontconfig and the fonts for the encodes I was doing picked up and registered fine - off a mostly-stock* LiveCD of 9.10, no less.

*I used UCK on it to include that mencoder build, libxvidcore4 1.2.2 from the Lucid repos, Medibuntu stuff, and all the other regular updates for Karmic.

Because of some MKV-specific eccentricities, it might be a little safer to also add the -ofps [23.976, 25, 29.97, etc.] parameter so that it converts VFR to CFR (if the stream is already CFR it probably won't hurt anything).  Most devices probably expect CFR video, and using -ofps makes sure mencoder keeps the audio in sync.

With mp4box, the command would look something like:
```
mp4box -add video.mp4 -add audio.aac output.mp4
```
There might be some more options needed if you're wanting to put them on a specific device, though.



However, unless something has dramatically changed, mencoder's output is borked if you use b-frames (and for H.264, you want to use b-frames), and that more than likely applies for any container, not just MP4.  You can get around that by piping mencoder's or mplayer's output to x264 (as long as x264 was compiled with GPAC) using yuv4mpeg, but it's been a long time since I had to do that and things never seemed to stay consistent (my preference would actually be piping from ffmpeg to x264 using yuv4mpeg, but ffmpeg doesn't support libass as far as I can tell).  mencoder/mplayer would only be used to do the initial rendering, all the encoding would be done by x264 itself.

---

### Post by VertexPusher on 2010-02-10
> **lovinglinux said:**
> Just use that ppa. It's from the smplayer developer.
Don't get me wrong, I compile whatever I need whenever I need it. It's just that when doing support in this forum, I have to refer to some common baseline rather than my own home-brew stuff.

---

### Post by timinator94 on 2010-04-30
Ahh thanks i just installed format factory using wine... that did the trick:guitar:

---

