---
title: "Record audio Desktop with ffmpeg"
date: 2010-03-22
forum: Multimedia Software
---

### Post by Hizoka on 2010-03-22
Hi,

I creating a mini soft for screencast (audio + video) with ffmpeg.

For the video, it's ok.

For the sound, the capture of sound of my webcam (/dev/dsp1) it's ok.
```
ffmpeg -f oss -ar 44100 -i /dev/dsp1 -acodec mp2 -ab 128k test.mp3
```

But for my audio desktop :
```
ffmpeg -f oss -ar 44100 -i /dev/dsp -acodec mp2 -ab 128k test.mp3
```
The file is empty...

I have make many test but... (find on internet)
```
ffmpeg -f oss -ar 44100 -ac 1 -i /dev/dsp -acodec pcm_s16le mumuv-050-mono.wav
```
```
ffmpeg -f oss -ar 44100 -ac 1 -i /dev/audio -acodec pcm_s16le mumuv-050-mono.wav
```
nothing works...

Other test with multi soft :
```
sox -t alsa "hw:0,0" -t ogg -A -2 -c1 -r11025 - | ffmpeg -y -i - -ar 11025 -ab 52 -ac 1 -f x11grab -s 800x600 -i :0.0+10,20 -b 200 -r 12 -aspect 4:3 -f flv test.flv
```
```
arecord -D hw:42 -f S16_LE -r 12345 -c 2 > file.wav
```
```
arecord --quiet --file-type wav --rate=44000 > test.wav
```

Test with alsa... :
```
ffmpeg -f alsa -r 16000 -i hw:2,0 -acodec libmp3lame -ab 96k output.avi

FFmpeg version SVN-r19468, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --libdir='${prefix}/lib' --shlibdir='${prefix}/lib' --bindir='${prefix}/bin' --incdir='${prefix}/include/ffmpeg' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir='${prefix}/share/man' --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libtheora --enable-libdc1394 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-avfilter-lavf --enable-libopenjpeg --enable-version3 --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Nov 16 2009 20:16:27, gcc: 4.4.1
Unknown input or output format: alsa
```
don't work again...

Does anybody know how I can do?

Thank's and sorry+++ for my English.

---

### Post by Hizoka on 2010-03-23
up please

---

### Post by andrew.46 on 2010-03-23
Hi Hizoka,

Your english looks pretty good to me :). I am no expert on capturing the screen in this manner but can I direct you to the following guide which speaks in great depth on this matter:

HOWTO: Proper Screencasting on Linux
[http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)

Hope this helps?

Andrew

---

### Post by Hizoka on 2010-03-24
Thank's for your answer.

I read this but it's the same thing...

The command :
```
ffmpeg -f alsa -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```
works on your desktop ?

In my desktp, no...
```
FFmpeg version SVN-r19468, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --libdir='${prefix}/lib' --shlibdir='${prefix}/lib' --bindir='${prefix}/bin' --incdir='${prefix}/include/ffmpeg' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir='${prefix}/share/man' --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libtheora --enable-libdc1394 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-avfilter-lavf --enable-libopenjpeg --enable-version3 --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Nov 16 2009 20:16:27, gcc: 4.4.1
Unknown input or output format: alsa
```
> If your distribution does not use the pulseaudio sound system, replace “-i pulse” with “-i /dev/dsp”.
I do...

Do I install other packages ?


I use Kubuntu 64bits 9.10


Thank's !

---

### Post by Hizoka on 2010-03-25
up please

---

### Post by Hizoka on 2010-03-31
up

---

### Post by Hizoka on 2010-04-07
up snifff

---

### Post by meklu on 2010-08-02
To find out if you actually have a sound device called pulse, you run "aplay -L".
If you have pulse you should install the package "pavucontrol".
When you're recording, open up pavucontrol and set the capture device from "<whatever the heck your soundcard is>" to "Monitor of <whatever the heck your soundcard is>".
Hope that helps.

---

### Post by Genserowski on 2011-03-14
Does not work for me :/

[http://pastebin.com/QTRcncHB](http://pastebin.com/QTRcncHB)

---

