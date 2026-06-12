---
title: "converting mp4 to avi"
date: 2012-12-18
forum: Multimedia Software
---

### Post by kabukiM0n0 on 2012-12-18
Hey guys. 

I'm attempting at converting huge 1080p .mp4 files into smaller, more compact .avi

WinFF and ConvertMe! don't seem to do absolutely nothing, even though they state that it has been converted *shrugs* 

I normally convert my .rm files to .avi with mencoder with the following. 
```
mencoder video1.rm -oac mp3lame -ovc xvid -xvidencopts bitrate=150 -srate 44100 -af resample=44100 -o video1.avi
```

Is there a simple way to do this but from .mp4?

Thank you! :popcorn:

K.m

---

### Post by cwsnyder on 2012-12-18
First, you should be aware that an .avi file IS an .mp4 file.

The only way you will make your 1080p.mp4 file smaller is to re-sample it at a lower resolution, or lower bit-rate, and even that may not make a huge difference in the file size.  Definitely your presets in WinFF for mp4 to .avi will not work, you will have to change the settings in the command-line for mencoder.

---

### Post by andrew.46 on 2012-12-19
The avi container is just about obsolete, do you have a reason apart from size that you need avi? If you are dead keen on avi I suspect FFmpeg will be your friend and the syntax could be suggested to you if you install it and then interrogate your file as follows:

```
ffmpeg -i **[COLOR="Red"]myfile[/COLOR]**
```

and then post the full terminal output here...

---

### Post by kabukiM0n0 on 2012-12-19
> **andrew.46 said:**
> The avi container is just about obsolete, do you have a reason apart from size that you need avi? If you are dead keen on avi I suspect FFmpeg will be your friend and the syntax could be suggested to you if you install it and then interrogate your file as follows:

```
ffmpeg -i **[COLOR="Red"]myfile[/COLOR]**
```

and then post the full terminal output here...

Doesn't have to be specifically avi - it's the 'normal' format my files are in, but I am open to others, as long as they function properly. 
I'm just trying to break the size of the files down. It from a DVD rip with 14 files and it's just immensely huge; 27.6GB

This is the reply I get from your code
```
ffmpeg -i /home/km/Downloads/Vuze/Done/Fashionistas/8310_01_1080p.mp4
ffmpeg version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:50:25 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (2997/50) -> 29.97 (2997/100)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/km/Downloads/Vuze/Done/Fashionistas/8310_01_1080p.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    creation_time   : 1970-01-01 00:00:00
    encoder         : Lavf52.93.0
  Duration: 00:45:20.15, start: 0.000000, bitrate: 7109 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 7001 kb/s, 29.97 fps, 29.97 tbr, 2997 tbn, 59.94 tbc
    Metadata:
      creation_time   : 1970-01-01 00:00:00
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 101 kb/s
    Metadata:
      creation_time   : 1970-01-01 00:00:00
At least one output file must be specified

```

---

### Post by dannyboy79 on 2012-12-19
you could use avidemux to encode it down to a more reasonable resolution and bitrate, that's the only way you'll get the file to be smaller. i believe in avidemux you can set the file size limit and it'll do the rest.

---

### Post by qamelian on 2012-12-19
> **cwsnyder said:**
> First, you should be aware that an .avi file IS an .mp4 file.
Not always. AVI files are just containers. The type of video in an avi is determined by the codec used to create it. It might be mp4, but could just as easily be mpeg 1, mpeg2, or any of a number of different codecs.

---

### Post by kabukiM0n0 on 2012-12-19
> **dannyboy79 said:**
> you could use avidemux to encode it down to a more reasonable resolution and bitrate, that's the only way you'll get the file to be smaller. i believe in avidemux you can set the file size limit and it'll do the rest.

It doesn't seem to work. 

When I open up the file, I'm prompted with the following. [HTML]H.264 detected

If the file is using B-frames as reference it can lead to a crash or stuttering.
Avidemux can use another mode which is safe but YOU WILL LOSE FRAME ACCURACY.
Do you want to use that mode?[/HTML]

If I accept and use safe-mode, once it is done. The file plays by frames. 

If I cancel. I'm prompted with [HTML]Index is not up to date

You should use Tool->Rebuild frame. Do it now ?[/HTML]

And then with [HTML]Crash

Assert failed :0
 at line 386, file /build/buildd/avidemux-2.5.4/avidemux/ADM_encoder/adm_encConfig.cppADM_backTrack
videoCodecGetMode()
ADM_Composer::saveAsScript(char const*, char const*)
saveCrashProject()
ADM_backTrack
ADM_Composer::getUncompressedFrame(unsigned int, ADMImage*, unsigned int*)
admPreview::update(unsigned int)
avidemux2_gtk() [0x808daae]
avidemux2_gtk() [0x809012c]
FileSel_ReadWrite(void (*)(char const*), int, char const*, char const*)
avidemux2_gtk() [0x8164c59]
GUI_FileSelRead(char const*, void (*)(char const*))
HandleAction(Action)
guiCallback(_GtkMenuItem*, void*)
g_cclosure_marshal_VOID__VOIDv

g_signal_emit_valist
g_signal_emit_by_name

g_cclosure_marshal_VOID__VOIDv[/HTML]
regardless whether I build or not.

---

### Post by Merrattic on 2012-12-19
Have a look here

[http://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide#twopass](http://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide#twopass)

You can choose your output filesize with two pass x264 encoding.

You will need to compile x264 then ffmpeg for this to work well. See here for guide:

[http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

---

### Post by evilsoup on 2012-12-19
You'd be best off turning an MP4 into a smaller MP4, than turning it into an AVI.

First, install avconv (the fork of ffmpeg included in the Ubuntu repositories):

```
sudo apt-get install avconv ubuntu-restricted-extras
```To convert the video:
```
avconv -i input.mp4 -an -c:v libx264 -crf 23 -preset veryfast output.mp4
```X264 is the open-source h.264 encoder, and is a rare case of an open-source implementation that is better than all the commercial products.

 -crf sets the quality: 0 is completely lossless, 18 is 'visually lossless', 23 is the default, and 26-28 (depending on who you ask) is the highest you should go, beyond there the visual quality is too bad to watch. A higher crf number will also give you smaller files; an increase of 6 should reduce file size by about half, so all other things being equal, -crf 26 will give you a file half the size of -crf 20.

 -preset sets the x264 preset: the available presets are ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow - the slower presets will give you a longer encoding time, but smaller output files. I tend to use veryfast, because after that IMO you get a case of diminishing returns (longer and longer encode times for less and less improvements in file size). You should use the slowest preset you can wait for.

I've left the audio to copy over the stream. The MP4 container can use AC3 (for surround sound) or AAC audio. If you want to compress the audio, I recommend using neroAacEnc. Unfortunately, it isn't open-source. Fortunately,  Nero have released it as free to use for personal uses. To install it, use:

```
wget ftp://ftp6.nero.com/tools/NeroDigitalAudio.zip
unzip NeroDigitalAudio.zip -d nero
cd nero/linux
sudo install -D -m755 neroAacEnc /usr/local/bin
```Unfortunately, it only takes wav input, so you have to pipe the input to it with avconv.

```
avconv -i input.mp4 -vn -f wav - | neroAacEnc -if - -ignorelength -q 0.5 -of intermediate.m4a
```If you want to mix 5.1 surround sound audio to stereo (will reduce file size, probably a good idea for listening on headphones):

```
avconv -i input.mp4 -vn -filter 'channelmap=map=DL-FL\,DR-FR' -f wav - | neroAacEnc -if - -ignorelength -q 0.5 -of intermediate.m4a
``` -q works in a similar way to x264's -crf: it dictates the quality and size of the AAC audio. 0 is worst quality, 1 is best. You can probably reduce it to 0.4 or 0.35 without any noticeable loss in audio quality.

Then, encode the video and mux in the the newly-created AAC audio:

```
avconv -i input.mp4 -i intermediate.m4a -map 0:v -map 1:a -c:a copy -c:v libx264 -crf 23 -preset veryfast output.mp4
``` -map 0:v -map 1:a tells avconv to take the video from input 0 (input.mp4) and audio from input 1 (intermediate.m4a). When that's done, you can safely delete intermediate.m4a.

To test out this video encoding settings on a section of video, use -ss and -t, like so:

```
avconv -i input.mp4 -i intermediate.m4a -map 0:v -map 1:a -c:a copy -c:v libx264 -crf 23 -preset veryfast -ss 00:10:00 -t 00:03:00 output.mp4
```This will encode a three minute clip, starting at ten minutes into the video.

Alternatively, you can install HandBrake from [this PPA]("https://launchpad.net/~stebbins/+archive/handbrake-releases"), and then do the whole thing with a nice & friendly GUI.

---

