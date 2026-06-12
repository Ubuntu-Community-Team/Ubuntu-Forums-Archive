---
title: "Encodng For Android"
date: 2010-08-18
forum: Multimedia Software
---

### Post by Cadmus on 2010-08-18
So, I've got myself a shiny new HTC Wildfire and want to get on with the serious business of putting some entertainment on it for use on long journeys.

On my Windows box I have used Avidemux and Handbrake and gotten the results I wanted. However I have a (effectively) headless Ubuntu server and I'd like to put that to good use, it would also mean I can happily set very long encodes going and leave it be.

I've read the guide at [the wiki]("https://help.ubuntu.com/community/AndroidVideoEncoding") but not being so au fait with video encoding (I know the basics) and the guide seemingly being written more for the GUI-based apps I was hoping someone here could point me towards understanding the command line tools better, or helping me 'convert' my Avidemux options I use on Windows into a command line format.

---

### Post by ron999 on 2010-08-18
Try the ffmpeg command in the wiki first.
Here:-[https://help.ubuntu.com/community/AndroidVideoEncoding#Expert%20mode:%20Using%20ffmpeg%20%28command%20line%29]("https://help.ubuntu.com/community/AndroidVideoEncoding#Expert%20mode:%20Using%20ffmpeg%20%28command%20line%29")

MPEG-4 will convert quickest.
H264 will give a smaller file size but will take longer to convert.

---

### Post by Cadmus on 2010-08-18
Thanks, re-reading it did help more than I thought. One problem is I don't seem to have AAC, I think I've got the Medibuntu repo set up right (mencoder has AAC available now) but for some reason ffmpeg doesn't. Is there a different package name? Or should I manually put in the version from medibuntu?

---

### Post by ron999 on 2010-08-18
What do you see when you enter:-
```
ffmpeg
```

---

### Post by Cadmus on 2010-08-18
```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --

extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib 

--enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads 

--enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --

enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 

49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  

libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on 

Mar  4 2010 12:41:55, gcc: 4.4.3
At least one output file must be specified

```

I have this sneaking suspicion...

---

### Post by ron999 on 2010-08-18
> **Cadmus said:**
> [CODE]

I have this sneaking suspicion...

I expected to see **--enable-libfaac**.

Never mind, did you enable the Medibuntu repository?
Option C here:-[http://ubuntuforums.org/showthread.php?t=1117283]("http://ubuntuforums.org/showthread.php?t=1117283")

---

### Post by Cadmus on 2010-08-18
Thanks for all your help here. I've got Medibuntu set up (see screen grab) and the medibuntu key-ring package installed. I've put on the libavcodec-extra-52 and that went fine.

I've done a purge and reinstall of ffmpeg and the codec and there's still no line referring to libfaac.

---

### Post by ron999 on 2010-08-18
> **Cadmus said:**
> 
... and there's still no line referring to libfaac.

That's correct.
It would show --enable libfaac only if ffmpeg had been compiled with it.

If you're sure that you followed fakeoutdoorsman's instruction about Medibuntu then try your command again.
Try using aac
or faac
or libfaac

---

### Post by Cadmus on 2010-08-18
Many thanks, 'libfaac' was today's secret word.

Now all I need to do is figure out settings, is the ffmpeg site the best place for such things or is there a better resource you know of?

---

### Post by ron999 on 2010-08-18
I don't know any particular resources, apart from Google.
Probably those basic commands for mpeg and x264 in the wiki will be OK.

---

### Post by papibe on 2010-08-18
I was following this very interested thread, but I got lost :(.

How did you solve the lack of aac on ffmpeg?

I have Medibuntu on my sources, but:
```
$ apt-cache search libfaac
libfaac-dev - an AAC audio encoder - devel files
libfaac0 - an AAC audio encoder - library files

$ sudo apt-get install libfaac0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libfaac0 is already the newest version.
libfaac0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

but no acc on ffmpeg. Would it be because ffmpeg got installed when I installed WinFF?

Thanks in advance.

---

### Post by ron999 on 2010-08-18
Solution was probably using **libfaac** command instead of aac.

What do you see when you enter
```
faac -h
```

---

### Post by papibe on 2010-08-18
Well, it wasn't installed, but after I did:
```
pablo@vaughan:~$ faac -h
Freeware Advanced Audio Coder
FAAC 1.26.1 (Aug 16 2008) UNSTABLE

Usage: faac [options] infiles ...
Options:
  -q <quality>	Set quantizer quality.
  -b <bitrate>	Set average bitrate to x kbps. (ABR, lower quality mode)
  -c <freq>	Set the bandwidth in Hz. (default=automatic)
  -o X		Set output file to X (only for one input file)
  -r		Use RAW AAC output file.
  -P		Raw PCM input mode (default 44100Hz 16bit stereo).
  -R		Raw PCM input rate.
  -B		Raw PCM input sample size (8, 16 (default), 24 or 32bits).
  -C		Raw PCM input channels.
  -X		Raw PCM swap input bytes
  -I <C,LF>	Input channel config, default is 3,4 (Center third, LF fourth)

MP4 specific options:
  -w		Wrap AAC data in MP4 container. (default for *.mp4 and *.m4a)
  --artist X	Set artist to X
  --writer X	Set writer to X
  --title X	Set title to X
  --genre X	Set genre to X
  --album X	Set album to X
  --compilation	Set compilation
  --track X	Set track to X (number/total)
  --disc X	Set disc to X (number/total)
  --year X	Set year to X
  --cover-art X	Read cover art from file X
  --comment X	Set comment to X

Documentation:
  --license	Show the FAAC license.
  --help	Show this abbreviated help.
  --long-help	Show complete help.

  More tips can be found in the audiocoding.com Knowledge Base at
  <http://www.audiocoding.com/wiki/>
```

sorry, but I still don't follow.

---

### Post by ron999 on 2010-08-18
> **papibe said:**
> Well, it wasn't installed, but after I did:
```
pablo@vaughan:~$ faac -h
Freeware Advanced Audio Coder
FAAC 1.26.1 (Aug 16 2008) UNSTABLE


```

sorry, but I still don't follow.

The aac encoder that's installed is named faac (not aac).

So when using the commands it's like this:-
```
ffmpeg -i source-video.avi -s 480x320 -vcodec mpeg4 -acodec **[COLOR="Red"]libfaac[/COLOR]** -ac 1 -ar 16000 -r 13 -ab 32000 -aspect 3:2 output-video.G1.mp4

```

---

### Post by papibe on 2010-08-18
Thanks! :-)

---

