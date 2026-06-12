---
title: "Video stablization with Transcode"
date: 2014-12-31
forum: Multimedia Software
---

### Post by pieman711 on 2014-12-31
I've recently bought a GoPro camera and have been playing with the video I have made. The biggest issue at the moment is reducing shake without reducing quality. I've been playing with transcode via the cli using
```
transcode -J stabilize -i yourmovie.avi
```
then
```
transcode -J transform  -i yourmovie.avi -y dvix -o yourstabilizedmovie.avi
```

The output quality is really poor. The initial file size is about 70mb and the out put is 10mb. I am recording in 1080p.  Is there any way of improving the output quality?
Thanks

---

### Post by Kirboosy on 2014-12-31
I would recommend trying ffmpeg or avconv. (libav ships by default since Ubuntu 14.04) That might give you better results than using dvix.

So the transform line might look something like this.

```
transcode -J transform -i yourmovie.avi -y avconv -o stabilizedmovie.avi
```
or
```
transcode -J transform -i yourmovie.avi -y ffmpeg -o stabilizedmovie.avi
```

Also depending on your videos shakiness you can increase the "shakiness parameter" until you get the desired results. Another way to achieve it would be run two passes on the file.

```
transcode -J stabilize=shakiness=8:show=1,preview -i youmovie.avi -y ffmpeg -o stablizedmovie.avi
```

I think it will come down to a lot of trial and error to find out what is the perfect flags for your video.

You can install FFmpeg still by adding their PPA: [URL="https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media"]FFmpeg release PPA
[/URL]
Hope that helps!
~Caboose

---

### Post by Rob Sayer on 2014-12-31
I just had a quick peek here:

[http://www.transcoding.org/transcode?Transcode](http://www.transcoding.org/transcode?Transcode)

and I'd want to try something different too.

I haven't used motion stabilization plugins.  But don't expect miracles.

And since you can't do something like that without re encoding it is actually impossible to do it with no quality loss.  Whatever quality loss is acceptable to you is up to you.

The obvious issue is that the input file is 7 times bigger than the output.  The bit rate is too low.

But there are many possible issues.  And video encoding isn't simple.  If I were you I'd try avidemux or handbrake.  From what I can see GUI tools may be more suitable, and they have a good balance between ease of use and power.

---

### Post by pieman711 on 2015-01-01
Thanks for that input. I'll have a play and see what I can do. I've tried using the ffmpeg flag but it would fail just before the end with abb invalid pointer error. I'll try again in a bit and see what I can do.

---

### Post by andrew.46 on 2015-01-03
Transcode has been quiescent for some time now so perhaps not the best choice. There is however an FFmpeg filter which I must admit I have zero experience with: [deshake]("http://ffmpeg.org/ffmpeg-filters.html#deshake"). See if your copy has access to this filter as follows:

```

andrew@ilium~$ **[COLOR="#FF0000"]ffmpeg -filters 2>/dev/null | grep deshake[/COLOR]**
 ... deshake          V->V       Stabilize shaky video.
andrew@ilium~$ 

```

Might be worth a go?

---

### Post by Rob Sayer on 2015-01-03
According to this:

[https://kdenlive.org/tutorial/how-use-video-stabilize-feature](https://kdenlive.org/tutorial/how-use-video-stabilize-feature)

Kdenlive has a deshake feature.  It's a big, complex editor, and will pull in KDE dependencies on a non KDE system, but at least it's a GUI.  And it's pretty well documented.

---

### Post by FakeOutdoorsman on 2015-01-03
FFmpeg also has [vidstabdetect](https://ffmpeg.org/ffmpeg-filters.html#vidstabdetect) and [vidstabtransform](https://ffmpeg.org/ffmpeg-filters.html#vidstabtransform). Requires your ffmpeg to be built with --enable-libvidstab. See the [FFmpeg Ubuntu Compile Guide](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu) for compile help (doesn't include libvidstab, but you can probably figure it out).

The [vid.stab](http://public.hronopik.de/vid.stab/) page has some video examples. Looks like it's in transcode too, but I'm not sure about the version in the repo.

---

### Post by pieman711 on 2015-01-05
When I try and use ffmpeg with transcode it always crashes at the end with the following out put. I've tried with a few different options for -F but the results are always the same (see the output below).
Rob said the bit rate is too low. Is there anyway of altering that?
Also the out put of 
```
ffmpeg -filters 2>/dev/null | grep deshake
```

Is nothing. 

Thanks for all of your help on this.

```

pieman@pieman-desktop:~/Videos/Test$ transcode -i GOPR0324.MP4 -y ffmpeg -F mpeg1video -o test4
transcode v1.1.7 (C) 2001-2003 Thomas Oestreich, 2003-2010 Transcode Team
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.BU.
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.BU.
[transcode] V: auto-probing     | GOPR0324.MP4 (OK)
[transcode] V: import format    | (null) in QuickTime (module=mov)
[transcode] A: auto-probing     | GOPR0324.MP4 (OK)
[transcode] A: import format    | PCM in QuickTime (module=mov)
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | 1920x1080  1.78:1  encoded @ 16:9
[transcode] V: bits/pixel       | 0.017 (low)
[transcode] V: decoding fps,frc | 50.000,6
[transcode] V: video format     | YUV420 (4:2:0) aka I420
[transcode] A: import format    | 0x1     PCM          [48000,16,2]
[transcode] A: export format    | 0x55    MPEG ES Layer 3 [48000,16,2]  128 kbps
[transcode] V: export format    | unknown (module dependant)
[transcode] V: encoding fps,frc | 50.000,6
[transcode] A: bytes per frame  | 3840 (3840.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse42 sse41 ssse3 sse3 sse2 sse mmx cmove asm 
[transcode] V: video buffer     | 10 @ 1920x1080 [0x2]
[transcode] A: audio buffer     | 10 @ 48000x2x16
[import_mov.so] v0.1.3 (2005-12-04) (video) * | (audio) *
[export_ffmpeg.so] v0.3.18 (2008-11-29) (video) Lavc54.35.0 | (audio) MPEG/AC3/PCM
[import_mov.so] codec=mp4a, rate=48000 Hz, bits=16, channels=2, samples=733184
[import_mov.so] VIDEO: codec=avc1, fps=50.000, width=1920, height=1080, frames=764
[filter_levels.so] instance #1
[filter_levels.so] v1.2.0 (2007-06-07) Luminosity level scaler
[filter_levels.so] scaling 0-255 gamma 1.000000 to 16-240 (pre-process)
[export_ffmpeg.so] Using FFMPEG codec 'mpeg1video' (FourCC 'mpg1', MPEG1 compliant video).
[export_ffmpeg.so] No profile selected
[export_ffmpeg.so] warning: Error opening configuration file ./ffmpeg.cfg: No such file or directory
[export_ffmpeg.so] Starting 1 thread(s)
[export_ffmpeg.so] Set display aspect ratio to input
[mpeg1video @ 0x2523320] removing common factors from framerate
[export_ffmpeg.so] warning: Usage of this module for audio encoding is deprecated.
[export_ffmpeg.so] warning: Consider switch to export_tcaud module.
[transcode] Audio: using lame-3.99.5
*** Error in `transcode': munmap_chunk(): invalid pointer: 0x00007f0aaa854e7a ***
Aborted (core dumped)
pieman@pieman-desktop:~/Videos/Test$
```

---

### Post by Rob Sayer on 2015-01-06
> **pieman711 said:**
> v...the bit rate is too low. Is there anyway of altering that? ...

Well, yes, there always is in an encoder.  I don't know what that setting is in CLI ffmpeg.

I've never actually had to use a CLI encoder.  And frankly if you don't know what the bit rate means, you probably shouldn't either.

Video encoding is actually quite complex.  There are tools that make it look easier but they don't work well ... the way you make things easier is to remove optione ie. features.

The thing that makes it hard is that there are no universal best encoding settings for all videos.  Digital media forums are full of newbies wanting those magic settings.  They don't exist.  You can't assume that simply cutting and pasting CLI commands will work right for something like this.

Really, you'd make your life easier if you find a GUI solution.  I'm not against using the terminal.  My first real computer was pre Windows.  But not for this unless absolutely necessary.  Just look at your VLC advanced settings.  With digital video you go straight from easy GUI level to video geek stuff.

---

### Post by pieman711 on 2015-01-06
Thanks Rob. I've had a very quick play with kdenlive and my first attempt was the best result I've got so far. Hopefully my solution will lie in there.

---

