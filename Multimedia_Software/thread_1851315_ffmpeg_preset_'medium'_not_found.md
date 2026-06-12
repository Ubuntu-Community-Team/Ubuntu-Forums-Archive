---
title: "ffmpeg preset 'medium' not found"
date: 2011-09-28
forum: Multimedia Software
---

### Post by tg3793 on 2011-09-28
Tried to use the following to convert a .OGV to a .AVI

```
ffmpeg -i foo.ogv -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec libfaac foo.avi
```

and got an error about "preset 'medium' not found". Further research advised me that there might be a problem with my version of ffmpeg so I used [this script]("http://www.prupert.co.uk/2011/04/07/a-better-ffmpeg-progress-script/") to uninstall it and compile the latest version.

That didn't fix the problem; am still getting the error about preset medium not being found.

For additional reference here it the output of my "ffmpeg -version":

```

ffmpeg version N-32845-g87f5e79, Copyright (c) 2000-2011 the FFmpeg developers
  built on Sep 24 2011 20:40:45 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libmp3lame
  libavutil    51. 17. 0 / 51. 17. 0
  libavcodec   53. 17. 0 / 53. 17. 0
  libavformat  53. 13. 0 / 53. 13. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 43. 5 /  2. 43. 5
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
ffmpeg N-32845-g87f5e79
libavutil    51. 17. 0 / 51. 17. 0
libavcodec   53. 17. 0 / 53. 17. 0
libavformat  53. 13. 0 / 53. 13. 0
libavdevice  53.  4. 0 / 53.  4. 0
libavfilter   2. 43. 5 /  2. 43. 5
libswscale    2.  1. 0 /  2.  1. 0
libpostproc  51.  2. 0 / 51.  2. 0


```

Thanks for any help here.

---

### Post by tg3793 on 2011-09-28
And in case someone is curious as to the code I used to compile ffmpeg; here it is:

```

#install ffmpeg
lucid_ffmpeg ()
{
cd $INSTALL 2>> $LOG >> $LOG
git clone git://git.videolan.org/ffmpeg 2>> $LOG >> $LOG
cd ffmpeg 2>> $LOG >> $LOG
./configure --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libmp3lame 2>> $LOG >> $LOG
make -j $NO_OF_CPUCORES 2>> $LOG >> $LOG
checkinstall --pkgname=ffmpeg --pkgversion="5:$(./version.sh)" --backup=no --deldoc=yes --default 2>> $LOG >> $LOG
hash x264 ffmpeg ffplay ffprobe 2>> $LOG >> $LOG
}

```

---

### Post by ron999 on 2011-09-28
Hi
The syntax has changed.
Try with "-preset" instead of "-vpre"
```
ffmpeg -i foo.ogv -vcodec libx264 -preset medium -crf 24 -threads 0 -acodec libfaac foo.avi
```
(Also consider using mp4 format instead of avi for x264).
```
ffmpeg -i foo.ogv -vcodec libx264 -preset medium -crf 24 -threads 0 -acodec libfaac foo.mp4
```

---

### Post by tg3793 on 2011-09-28
I have a lot of reasons to prefer the command line, however while I was searching for this answer I found [Arista Transcoder]("www.transcoder.org") and it did a really great job for a GUI.

In order to make use of the newest presets you'll want to get the latest version directly from the website. For those that don't know how to install it; you navigate to the directory that you uncompressed "arista-0.9.7.tar.gz" to and:

cd /path/to/arista-0.9.7/
sudo python setup.py install --install-layout=deb

Hope this will help others that might be struggling with this. But I will certainly try some of these command line options as soon as I get some extra time. For now I'm about two days behind on some editing and conversions I need to do; thanks.

---

### Post by andrew.46 on 2011-09-28
FFmpeg now uses x264 presets, which can be seen with *x264 --fullhelp*:

```

--preset <string>       Use a preset to select encoding settings [medium]
                                  Overridden by user settings.
                                  - **[COLOR="Red"]ultrafast[/COLOR]**:
                                    --no-8x8dct --aq-mode 0 --b-adapt 0
                                    --bframes 0 --no-cabac --no-deblock
                                    --no-mbtree --me dia --no-mixed-refs
                                    --partitions none --rc-lookahead 0 --ref 1
                                    --scenecut 0 --subme 0 --trellis 0
                                    --no-weightb --weightp 0
                                  - **[COLOR="Red"]superfast[/COLOR]**:
                                    --no-mbtree --me dia --no-mixed-refs
                                    --partitions i8x8,i4x4 --rc-lookahead 0
                                    --ref 1 --subme 1 --trellis 0 --weightp 1
                                  - **[COLOR="Red"]veryfast[/COLOR]**:
                                    --no-mixed-refs --rc-lookahead 10
                                    --ref 1 --subme 2 --trellis 0 --weightp 1
                                  - **[COLOR="Red"]faster[/COLOR]**:
                                    --no-mixed-refs --rc-lookahead 20
                                    --ref 2 --subme 4 --weightp 1
                                  - **[COLOR="Red"]fast[/COLOR]**:
                                    --rc-lookahead 30 --ref 2 --subme 6
                                    --weightp 1
                                  - **[COLOR="Red"]medium[/COLOR]**:
                                    Default settings apply.
                                  - **[COLOR="Red"]slow[/COLOR]**:
                                    --b-adapt 2 --direct auto --me umh
                                    --rc-lookahead 50 --ref 5 --subme 8
                                  - **[COLOR="Red"]slower[/COLOR]**:
                                    --b-adapt 2 --direct auto --me umh
                                    --partitions all --rc-lookahead 60
                                    --ref 8 --subme 9 --trellis 2
                                  - **[COLOR="Red"]veryslow[/COLOR]**:
                                    --b-adapt 2 --bframes 8 --direct auto
                                    --me umh --merange 24 --partitions all
                                    --ref 16 --subme 10 --trellis 2
                                    --rc-lookahead 60
                                  - **[COLOR="Red"]placebo[/COLOR]**:
                                    --bframes 16 --b-adapt 2 --direct auto
                                    --slow-firstpass --no-fast-pskip
                                    --me tesa --merange 24 --partitions all
                                    --rc-lookahead 60 --ref 16 --subme 11
                                    --trellis 2


```

Default is useful enough mind you... Now if I only knew what half of those options actually meant :(.

---

