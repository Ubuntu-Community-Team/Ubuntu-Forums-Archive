---
title: "[SOLVED] FFmpeg input video frame size"
date: 2008-08-16
forum: Multimedia Software
---

### Post by denham2010 on 2008-08-16
Hi,

I know this must seem like a simple question, but after googling for hours, I have still had no luck.

I am using ffmpeg to convert a lot of .avi files to .mp4. I need to have the .mp4 files at a specific frame size. This requires me to get the frame size of the input video, and perform some calculations to determine the amount of left/right or top/bottom padding needed to achieve the set output frame size (obviously in order to maintain the correct video aspect in the output frame size).

Currently I have to open the input video in Avidemux and check the properties to get the frame size, and then manually calculate the padding to put in my ffmpeg script.

I really want to automate this. What I need to know is how I can determine the input file's frame size so I can have the script automatically perform the padding calculation for me?

All assistance is appreciated.

---

### Post by cor2y on 2008-08-16
the most i can think of is using mplayer via the terminal to see your clip resolution  details etc.
Or right clicking on them and selecting properties and going to the audio/video tab in nautilus.
For Mplayer via the terminal
```
 mplayer -vo null -ao null -ss 0:00 -endpos 0:30  file.avi
```
This will display the resolution , runtime, video codec etc but not the movie (-ao null and -vo null means no audio and video outputs) and for a limited time (-ss 0.00 -endpos 0:30 means for only 30 seconds from the start of the movie) this should allow you enough time to see the details of the file.

---

### Post by denham2010 on 2008-08-16
Thanks Cor2y,

I modified your code a little bit to:

```
mplayer -vo null -ao null -ss 0:00 -endpos 0:00  file.avi > output.txt
```

This now creates a file I can open and extract the frame size, and it can be done from within my script.

Cheers!

---

### Post by eye208 on 2008-08-16
> **denham2010 said:**
> I really want to automate this.
You really want to use MEncoder instead of FFMPEG.

For example, to resize any video to 640x480 with automatic padding, specify these filters:
```
-vf expand=:::::4/3,scale=640x480
```

---

### Post by denham2010 on 2008-08-17
Thanks eye208,

I have tried many different encoding options, including MEncoder and Avidemux, all with the same settings. But the device I am playing the .mp4 files on seems very particular about the file it receives.

The only converted files I have successfully got to work on the device are those converted with ffmpeg. All the other conversions just lock the device up.

For interests sake, the device is an iPod Touch.

I have followed many tutorials and used many presets in different programs and scripts, but the only one that has worked is ffmpeg.

So I guess, I just want to stick with what I know works.

Attached is my script, far from perfect, but it works for batch processing .avi files for me.

It's a python script and depends on ffmpeg and mplayer. Hopefully someone else may find it useful.

Just make the file executable and in a terminal enter:

```
avitomp4.py -h
```

[ATTACH]81813[/ATTACH]

Cheers.

---

### Post by eye208 on 2008-08-17
> **denham2010 said:**
> I have tried many different encoding options, including MEncoder and Avidemux, all with the same settings. But the device I am playing the .mp4 files on seems very particular about the file it receives.

The only converted files I have successfully got to work on the device are those converted with ffmpeg. All the other conversions just lock the device up.

For interests sake, the device is an iPod Touch.
A Google search for ["mencoder ipod touch"](http://www.google.com/search?hl=en&q=mencoder+ipod+touch&btnG=Google+Search&aq=f&oq=) yielded [this](http://archives.free.net.ph/message/20071208.154834.50a983e8.en.html) as the first result:
> > I'm using MEncoder (1.0rc2) to encode videos for my iPod Touch. The
> following command line produces files that work perfectly fine:
>
> mencoder -ofps 25 -of lavf -lavfopts format=mp4 -af lavcresample=44100 -vf-add harddup -vf-add scale=480:-11 -oac lavc -ovc lavc -lavcopts aglobal=1:vglobal=1:acodec=libfaac:abitrate=128:vcodec=mpeg4:vbitrate=384:keyint=25 -o test.mp4 test.avi
>
> I do however believe that I could get improved quality by encoding in
> H.264 instead, and did the following obvious attempt:
>
> mencoder -ofps 25 -of lavf -lavfopts format=mp4 -af lavcresample=44100 -vf-add harddup -vf-add scale=480:-11 -oac lavc -ovc lavc -lavcopts aglobal=1:vglobal=1:acodec=libfaac:abitrate=128:vcodec=libx264:vbitrate=384:keyint=25 -o test.mp4 test.avi
>
> The files produced by that command line play fine in MPlayer and
> QuickTime Player but iTunes refuses to download them to the iPod.
>
> Does anyone know anything useful to help me out here?
>
iTunes won't download them to the ipod unless the "itunes" atom is set
to the correct value. You can add the atom to the file with nicMP4Box (
[http://nic.dnsalias.com/NicMP4Box.zip](http://nic.dnsalias.com/NicMP4Box.zip) )

nicmp4box -add test.mp4 final.mp4

I've posted my own personal recipe for ipod encoding on the list before, but here it is again:

mencoder INPUT -sws 9 -of lavf -lavfopts format=mp4
/ -vf scale=576:320,dsize=576:320,harddup
/ -ovc x264
/ -x264encopts bitrate=1381:vbv_maxrate=1500:vbv_bufsize=2000:nocabac:me=umh:
/trellis=1:level_idc=30:global_header:threads=2:pass=1:turbo
/ -oac faac
/ -faacopts mpeg=4:object=2:br=160:raw -channels 2 -srate 48000 -o TEMP.mp4

mencoder INPUT -sws 9 -of lavf -lavfopts format=mp4
/ -vf scale=576:320,dsize=576:320,harddup
/ -ovc x264
/ -x264encopts bitrate=1381:vbv_maxrate=1500:vbv_bufsize=2000:nocabac:me=umh:
/subq=6:frameref=6:trellis=1:level_idc=30:global_header:threads=2:pass=2
/ -oac faac
/ -faacopts mpeg=4:object=2:br=160:raw -channels 2 -srate 48000 -o TEMP.mp4

nicmp4box -add TEMP.mp4 OUTPUT.mp4
I looked at your script and saw that you use the Xvid codec with FFMPEG. You may want to try the H.264 solution described above for a boost in quality and resolution.

According to the example, the iPod Touch seems to expect H.264 video at 576x320 resolution, i.e. 16:9 picture aspect ratio. A suitable filter for automatic padding would look like this:
```
-vf expand=:::::16/9,scale=576:320,harddup
```

---

