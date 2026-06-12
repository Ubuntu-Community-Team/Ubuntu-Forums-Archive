---
title: "How to extend the duration of a movie?"
date: 2012-01-02
forum: Multimedia Software
---

### Post by Roger Allott on 2012-01-02
I have an avi video file that's 35 minutes 40 seconds duration. My problem is that whoever encoded it seems to have made a booboo, because it plays at something like double speed - both the video and audio. The file properties tell me that it's at 25 fps.

Let's call the file movie.avi

In Avidemux, there's a video filter to change the fps but without changing total duration. But that's not what I want. I want the duration changed, and I don't mind dropping the fps. And of course I need the audio to change duration as well.

Anyone have any ideas on how I can do that? Using ffmpeg, or PiTiVi, or Avidemux?

---

### Post by FakeOutdoorsman on 2012-01-03
Can you show us what FFmpeg says about the file?
```
ffmpeg -i movie.avi
```

---

### Post by Roger Allott on 2012-01-03
> **FakeOutdoorsman said:**
> Can you show us what FFmpeg says about the file?
```
ffmpeg -i movie.avi
```

Thanks for asking. Sorry for the delay, but I had an even bigger problem when Ubuntu steadfastly refused to boot! Anyway, now that I'm in, here's the output from that command:

```
$ ffmpeg -i movie.avi
FFmpeg version 0.6-4:0.6-2ubuntu6.2, Copyright (c) 2000-2010 the FFmpeg developers
  built on Sep 16 2011 17:11:24 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu3.2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mpeg4 @ 0x956de10]Invalid and inefficient vfw-avi packed B frames detected
[mp3 @ 0x956e800]Header missing

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 25.00 (25/1)
Input #0, avi, from 'movie.avi':
  Duration: 00:35:40.40, start: 0.000000, bitrate: 983 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x480 [PAR 1:1 DAR 3:2], 25 fps, 25 tbr, 25 tbn, 30k tbc
    Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16, 320 kb/s
At least one output file must be specified
```

---

### Post by FakeOutdoorsman on 2012-01-03
Does the movie play normally with ffplay?
```
ffplay movie.avi
```

The easiest thing to try is to re-mux it (possibly into a different container). I'm not sure if it will actually help:
```
ffmpeg -i movie.avi -vcodec copy -acodec copy output.avi
```
or
```
ffmpeg -i movie.avi -vcodec copy -acodec copy output.mkv
```

If not then you can always try to change the speed/duration as you suggested, but first you will probably have to compile FFmpeg because I believe pre-Natty versions from the repository do not include filtering capabilities:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

**Make the video half-speed:**
```
ffmpeg -i movie.avi -c:v libx264 -preset medium -crf 22 -vf setpts=2.0*PTS -an video.mp4
```

**Make the audio half-speed:**
```
ffmpeg -i movie.avi -f sox - | sox -t sox - -t wav - speed 2 | ffmpeg -i - -c:a libfaac -q:a 100 audio.mp4
```

**Combine (mux) the video and audio:**
```
ffmpeg -i video.mp4 -i audio.mp4 -c copy -shortest output.mp4
```
Assuming you wanted H.264 video and AAC audio in MP4.

---

### Post by Roger Allott on 2012-01-03
> **FakeOutdoorsman said:**
> Does the movie play normally with ffplay?
```
ffplay movie.avi
```
Well, normally as in at a much higher speed that it should be. i.e. no difference between that and what I get on other players.

> **FakeOutdoorsman said:**
> The easiest thing to try is to re-mux it (possibly into a different container). I'm not sure if it will actually help:
```
ffmpeg -i movie.avi -vcodec copy -acodec copy output.avi
```
or
```
ffmpeg -i movie.avi -vcodec copy -acodec copy output.mkv
```
I tried the first of those options and the output.avi file is only 2.2 MB and 18 seconds long. From the Terminal text I think it hit a problem at frame 711:
```
Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 25.00 (25/1)
Input #0, avi, from 'movie.avi':
  Duration: 00:35:40.40, start: 0.000000, bitrate: 983 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x480 [PAR 1:1 DAR 3:2], 25 fps, 25 tbr, 25 tbn, 30k tbc
    Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16, 320 kb/s
Output #0, avi, to 'output.avi':
  Metadata:
    ISFT            : Lavf52.64.2
    Stream #0.0: Video: mpeg4, yuv420p, 720x480 [PAR 1:1 DAR 3:2], q=2-31, 25 tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, 2 channels, 320 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[avi @ 0x9682bd0]st:1 error, non monotone timestamps 711 >= 711
av_interleaved_write_frame(): Operation not permitted
```


> **FakeOutdoorsman said:**
> If not then you can always try to change the speed/duration as you suggested, but first you will probably have to compile FFmpeg because I believe pre-Natty versions from the repository do not include filtering capabilities:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

**Make the video half-speed:**
```
ffmpeg -i movie.avi -c:v libx264 -preset medium -crf 22 -vf setpts=2.0*PTS -an video.mp4
```

**Make the audio half-speed:**
```
ffmpeg -i movie.avi -f sox - | sox -t sox - -t wav - speed 2 | ffmpeg -i - -c:a libfaac -q:a 100 audio.mp4
```

**Combine (mux) the video and audio:**
```
ffmpeg -i video.mp4 -i audio.mp4 -c copy -shortest output.mp4
```
Assuming you wanted H.264 video and AAC audio in MP4.

Booger! I hate having to do that! Oh well, it seems like it's my only option. I'll let you know how it goes.

---

### Post by FakeOutdoorsman on 2012-01-03
> **Roger Allott said:**
> Booger! I hate having to do that!
You could skip large sections of the guide if you want to and integration into the package management system can be considered optional too:

1. Dependencies
```
sudo apt-get install build-essential git libfaac-dev yasm
```
2. Install x264 as shown
3. Install FFmpeg
```
cd
git clone --depth 1 git://source.ffmpeg.org/ffmpeg
cd ffmpeg
./configure --enable-gpl --enable-nonfree --enable-libx264 --enable-libfaac
make -j2
```
4. Run FFmpeg:
```
cd ~/ffmpeg
./ffmpeg -i movie.avi ...
```

---

### Post by Roger Allott on 2012-01-04
> **FakeOutdoorsman said:**
> You could skip large sections of the guide if you want to and integration into the package management system can be considered optional too:

1. Dependencies
```
sudo apt-get install build-essential git libfaac-dev yasm
```


I'm getting an odd error message when I ran that.

```
build-essential is already the newest version.
git is already the newest version.
git set to manually installed.
The following NEW packages will be installed
  libfaac-dev yasm
0 upgraded, 2 newly installed, 0 to remove and 14 not upgraded.
Need to get 854kB of archives.
After this operation, 2,228kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ maverick/multiverse libfaac-dev i386 1.26-0.1ubuntu2 [64.2kB]
Get:2 http://archive.ubuntu.com/ubuntu/ maverick/main yasm i386 1.1.0-0ubuntu1 [789kB]
Fetched 854kB in 4s (183kB/s)
dpkg: too-long line or missing newline in `/var/lib/dpkg/triggers//File'
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Any ideas?

---

### Post by FakeOutdoorsman on 2012-01-04
> **Roger Allott said:**
> Any ideas?

Not really, unfortunately, but could you show the contents of:
```
cat /var/lib/dpkg/triggers//File
```
Do you see anything mental going on in the file?

If it's incredibly long, then the last bit of it might suffice:
```
tail /var/lib/dpkg/triggers//File
```

---

### Post by Roger Allott on 2012-01-04
> **FakeOutdoorsman said:**
> Not really, unfortunately, but could you show the contents of:
```
cat /var/lib/dpkg/triggers//File
```
Do you see anything mental going on in the file?

If it's incredibly long, then the last bit of it might suffice:
```
tail /var/lib/dpkg/triggers//File
```

Both commands are giving me back complete gobbledegook. e.g.

```
~$ tail /var/lib/dpkg/triggers//File
&#65533;)9i&#65533;&#65533;&#65533;&#65533;]6=[&#65533;W:&#65533;V&#65533;&#65533;&#65533;&#811;%&#65533;G&#65533;I(;&#65533;<&#31277;?x&#65533;&#65533;&#65533;&#65533;p&#65533;WT&#65533;
                                              ZCIw+N.&#65533;&#65533;&#65533;I&#65533;&#65533;&#65533;&#65533;&#65533;}Er&#65533;&#65533;=&#65533;Z&#1080;&#65533;SS&#65533;
&#65533;&#65533;&#65533;4S&#65533;&#65533;&#65533;	R&#65533;&#65533;<C&#65533;[&#65533;R&#65533;o
&#65533;X_E&#65533;D&#65533;Igq/&#65533;&#16682;&#65533;	
B&#65533;&#65533;R&#1260;M&#65533;&#65533;&#65533;&#65533;Yô&#65533;C'@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;<&#65533;&#65533;&#65533;Y&#65533;\&#65533;6&#65533;&#65533;&#65533;r&#65533;&#65533;d&#985;p&#65533;x&#65533;H&#65533;n&#65533;b&#65533;&#65533;z&#65533;LQDV&#65533;i*&#65533;dl&#65533;&#65533;&#65533;&#65533;n&#65533;&#65533;&#65533;^j&#65533;N&#65533;"&#65533;j&#65533;=l&#65533;&#65533;&#65533;]k&#65533;~_&#65533;H&#65533;?&#65533;=/H&#65533;&#65533;K&#65533;&#65533;w&#65533;&#65533;o&#65533;Sv72o&#65533;&#65533;I&#65533;q&#65533;x&#65533;5&#65533;&#65533;&#65533;&#65533;&#65533;`_Zx&#65533;N&#65533;$&#65533;&#65533;|&#65533;&#65533;
                                                                       [s&#65533;&#65533;&#65533;&#65533;OL&#65533;&#65533;}&#65533;KOS&#65533;J&#65533;-:9U-&#65533;v&#65533;X&#65533;&#65533;rvNx&#65533;&#65533;P&#65533;$&#65533;&#65533;V&#65533;&#65533;s&#65533;&#65533;&#65533; &#682;K
                                                    :x&#65533;&#65533;_&#65533;J&#65533;&#65533;Mm&#65533;&#65533;&#65533;,&#65533;+&#65533;&#65533;&#65533;&#65533;&#65533;]}/[&#65533;&#65533;q&#65533;-8&#65533;3NT&#65533;V&#65533;&#65533;N	&#65533;&#65533;\&#65533;&#65533;y&#65533;&#65533;&#65533;#&#65533;\O&#65533;%:&#65533;&#65533;&#65533;w,Q&#65533;sp&#65533;&#65533;&#65533;&#65533;,cq&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;
&#65533;9&#65533;c&#65533;&#65533;&#919;?&#65533;I&#65533;&#65533;e&#65533;&#65533;&#65533;&#65533;&#65533;`t&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;m9&#65533;&#65533;t&#65533;&#65533;]&#65533;&#65533;O&#65533;z&#65533;&#65533;&#65533;ue=&#65533;&#65533;&#65533;H&#65533;&#65533;&#65533;&#1786;c=
&#65533;&#65533;&#65533;zRR&#65533;&#65533;>F&#65533;zu&#65533;&#65533;&#291;&#65533;6&#65533;x&#65533;&#65533;&#65533;&#65533;&#65533;m&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;x&#65533;X&#65533;&#65533;5	&#65533;&#65533;&#65533;+&#65533;h1&#65533;&#65533;X&#799;'&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;!bV&#65533;^&#65533;&#65533;&#65533;^2&#65533;&#65533;&#65533;"&#65533;$&#65533;&#65533;Z&#65533;x<}&#65533;&#65533;QRD&#65533;&#1139;3&#65533; )A#;&#65533;&#65533;&#65533;]Z&#65533;!W&#65533;&#65533;	5&#65533;O&#65533;&#65533;G7&#65533;&#65533;&
                                                           x&#65533;H&#65533;Q&#65533;Oi&#1692;&#65533;o&#65533;&#65533;&#65533;r&#65533;'&#65533;s&#65533;:s[~#^&#65533;7rx7&#65533;&#65533;}&#65533;{&#65533;&#65533;&#65533;e&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;z&#65533;O&#65533;5&#65533;&#65533;&#65533;#&#65533;]z&#65533;]&#65533;&#65533;&#65533;&#60915;&#65533;&#65533;	&#65533;Evw&#65533;&#1951;k{qq&#65533;mgN&#65533;&#65533;Q&#65533;&#65533;{k&#65533;&#65533;)&#65533;~&#1100;&#65533;J&#65533;J&#65533;&#65533;&#65533;&#65533;#&#476;&#65533;&#65533;&#65533;qi[&#65533;w&#65533;
                                 &#65533;&#65533;&#65533;&#65533;a&#65533;&#65533;&#65533;&#970;,N&#65533;}[&#65533;&#65533;&#65533;E.&#497;T>&#65533;~@&#65533;&#65533;7&#65533;&#65533;8&i&#65533;&#65533;l&#65533;&#65533;
&#65533;pQ]&#65533;&#65533;E&#65533;&#65533;&#65533;s&#65533;&#65533;&#65533;&#65533;&#65533;&#1340;A&#65533;H4&#65533;&#65533;T&#65533;&#65533;&#65533;&#65533;&#65533;s)>&#65533;*I&#65533;8>T&#65533;s&#65533;G=k&#65533;&#65533;&#65533;u&#65533;&#65533;&#65533;s&#65533;&#1326;!&#65533;&#65533;&#65533;&#65533;Tk&#65533;&#65533;m&#65533;&#65533;&#65533;&#65533;-&#65533;&#65533;/&#65533;|&#65533;&#65533;&#65533;dL&#65533;r&#65533;&#65533;&#65533;i_&#679;&#65533;&#65533;<&#65533;&#65533;+%&#65533;&#65533;&#65533;Rm:&#65533;&#65533;&#65533;&#65533;cp<&#65533;3&#65533;U&#65533;&#65533;I&#65533;j&#65533;W&#65533;&#65533;&#65533;j*Q&#65533;&#63735;&#65533;&#65533;&#65533;>$&#65533;7i&#65533;&#65533;\&#65533;&#65533;&#65533;n%&#65533;&#65533;&#65533;J&#65533;Kg&#65533;&#65533;y&#65533;&#1832;&#65533;&#65533;	&#65533;n&#65533;&#65533;z&#1383;&#65533;W&#65533;m&#65533;&#65533;+dU&#976;&#65533;&#65533;&#65533;&#65533;b&#65533;/|&#&#65533;&#65533;wJ&#65533;&#65533;&#65533;w&#65533;&#65533;&#65533;N
```

---

### Post by FakeOutdoorsman on 2012-01-04
Strange. On my Maverick 10.10 (is that what you're on?) I have:
```
/etc/init ureadahead
/etc/init.d ureadahead
/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders libgdk-pixbuf2.0-0
/usr/share/fonts fontconfig
/usr/share/ghostscript/fonts fontconfig
/usr/share/texmf/fonts fontconfig
/usr/share/mime/packages shared-mime-info
/usr/lib/gtk-2.0/2.10.0/immodules libgtk2.0-0
/usr/share/gconf/defaults gconf2
/usr/share/gconf/mandatory gconf2
/usr/share/gconf/schemas gconf2
/usr/share/applications python-gmenu
/usr/share/icons/hicolor hicolor-icon-theme
/usr/share/icons/gnome gnome-icon-theme
/usr/share/applications desktop-file-utils
/usr/man man-db
/usr/share/man man-db
/usr/local/man man-db
/usr/local/share/man man-db
/usr/X11R6/man man-db
/opt/man man-db
/usr/share/info install-info
/etc/ufw/applications.d ufw
/usr/share/doc-base doc-base
/usr/share/app-install/desktop software-center
/usr/share/locale-langpack software-center
/usr/lib/gio/modules libglib2.0-0
/usr/share/glib-2.0/schemas libglib2.0-0
/usr/share/gconf/une/defaults ubuntu-netbook-default-settings
/usr/share/gconf/une/mandatory ubuntu-netbook-default-settings
/usr/share/applications bamfdaemon
```

or 11.04:
```
/usr/lib/i386-linux-gnu/gio/modules libglib2.0-0
/usr/lib/gio/modules libglib2.0-0
/usr/share/glib-2.0/schemas libglib2.0-0
/etc/init ureadahead
/etc/init.d ureadahead
/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders libgdk-pixbuf2.0-0
/usr/share/fonts fontconfig
/usr/share/ghostscript/fonts fontconfig
/usr/share/texmf/fonts fontconfig
/usr/share/mime/packages shared-mime-info
/usr/lib/gtk-2.0/2.10.0/immodules libgtk2.0-0
/usr/share/gconf/defaults gconf2
/usr/share/gconf/mandatory gconf2
/usr/share/gconf/schemas gconf2
/usr/share/GConf/gsettings gconf2
/usr/share/applications python-gmenu
/usr/share/icons/hicolor hicolor-icon-theme
/usr/share/icons/gnome gnome-icon-theme
/usr/share/applications desktop-file-utils
/usr/share/applications bamfdaemon
/usr/man man-db
/usr/share/man man-db
/usr/local/man man-db
/usr/local/share/man man-db
/usr/X11R6/man man-db
/opt/man man-db
/usr/share/info install-info
/etc/ufw/applications.d ufw
/usr/share/doc-base doc-base
/usr/lib/libreoffice/share/extensions libreoffice-common
/usr/share/locale/locale.alias lintian
/usr/lib/locales-all lintian
/usr/share/app-install/desktop software-center
/usr/share/locale-langpack software-center
```

I have no idea what this file does. Might be worth renaming it:
```
sudo mv /var/lib/dpkg/triggers/File{,.orig}
```
You could try installing stuff now, or make a new blank File, or try using the contents from mine. Just some uneducated guesses here because I have no idea and I didn't really research any of this...so it might be bad advice.

---

### Post by mc4man on 2012-01-04
If you rename then you'll be able to install again but probably not what you want to do.
I'd replace the current file (File) with the one FO posted for **10.10**

Ex. - 
with the "File" file removed - 
> ~$ sudo dpkg -i '/home/doug/Downloads/gnome-settings-daemon_3.2.2-0ubuntu2.1_i386.deb' 
[sudo] password for doug: 
dpkg: warning: downgrading gnome-settings-daemon from 3.2.2-0ubuntu6 to 3.2.2-0ubuntu2.1.
(Reading database ... 168229 files and directories currently installed.)
Preparing to replace gnome-settings-daemon 3.2.2-0ubuntu6 (using .../gnome-settings-daemon_3.2.2-0ubuntu2.1_i386.deb) ...
Unpacking replacement gnome-settings-daemon ...
Setting up gnome-settings-daemon (3.2.2-0ubuntu2.1) ...

With "File" in place

> ~$ sudo dpkg -i '/home/doug/Downloads/gnome-settings-daemon_3.2.2-0ubuntu2.1_i386.deb' 
dpkg: warning: downgrading gnome-settings-daemon from 3.2.2-0ubuntu6 to 3.2.2-0ubuntu2.1.
(Reading database ... 168229 files and directories currently installed.)
Preparing to replace gnome-settings-daemon 3.2.2-0ubuntu6 (using .../gnome-settings-daemon_3.2.2-0ubuntu2.1_i386.deb) ...
Unpacking replacement gnome-settings-daemon ...
Setting up gnome-settings-daemon (3.2.2-0ubuntu2.1) ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...


var/lib/dpkg/triggers/File is part of your base install, not sure if you can get it re-created so copying the one posted may be best way or copying from a **10.10** live session, they likely are  the same.

---

### Post by Roger Allott on 2012-01-05
> **FakeOutdoorsman said:**
> Strange. On my Maverick 10.10 (is that what you're on?) I have:
```
/etc/init ureadahead
/etc/init.d ureadahead
/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders libgdk-pixbuf2.0-0
/usr/share/fonts fontconfig
/usr/share/ghostscript/fonts fontconfig
/usr/share/texmf/fonts fontconfig
/usr/share/mime/packages shared-mime-info
/usr/lib/gtk-2.0/2.10.0/immodules libgtk2.0-0
/usr/share/gconf/defaults gconf2
/usr/share/gconf/mandatory gconf2
/usr/share/gconf/schemas gconf2
/usr/share/applications python-gmenu
/usr/share/icons/hicolor hicolor-icon-theme
/usr/share/icons/gnome gnome-icon-theme
/usr/share/applications desktop-file-utils
/usr/man man-db
/usr/share/man man-db
/usr/local/man man-db
/usr/local/share/man man-db
/usr/X11R6/man man-db
/opt/man man-db
/usr/share/info install-info
/etc/ufw/applications.d ufw
/usr/share/doc-base doc-base
/usr/share/app-install/desktop software-center
/usr/share/locale-langpack software-center
/usr/lib/gio/modules libglib2.0-0
/usr/share/glib-2.0/schemas libglib2.0-0
/usr/share/gconf/une/defaults ubuntu-netbook-default-settings
/usr/share/gconf/une/mandatory ubuntu-netbook-default-settings
/usr/share/applications bamfdaemon
```


Thanks for that. It seems obvious now that my problem is far bigger than re-encoding a video file! I simply cannot update anything at the moment.

A little query though is the lines near the bottom of your file seem to suggest that that's on a netbook variant of Ubuntu, whereas this PC is a laptop that I'm pretty sure is running the standard desktop variant.

For example, I've taken a peek at usr/share/gconf and there's no folder named une. The folders that are in gconf are named defaults, mandatory and schemas.

A second question is about how I go about re-creating that file, as it presumably has to have the root permissions and all that jazz, doesn't it? I presume that I can't just copy your text into a text editor and save it to the var/lib/dpkg/triggers folder, or can I?

---

### Post by Roger Allott on 2012-01-05
> **mc4man said:**
> If you rename then you'll be able to install again but probably not what you want to do.
I'd replace the current file (File) with the one FO posted for **10.10**

Ex. - 
with the "File" file removed - 


With "File" in place



var/lib/dpkg/triggers/File is part of your base install, not sure if you can get it re-created so copying the one posted may be best way or copying from a **10.10** live session, they likely are  the same.

Sorry for being a thickie, but are you suggesting that I should downgrade gnome-settings-daemon from 3.2.2-0ubuntu6 to 3.2.2-0ubuntu2.1? Or was that just an example of you showing that dpkg would work even if the File file were completely deleted?

---

### Post by mc4man on 2012-01-05
> **Roger Allott said:**
> Sorry for being a thickie, but are you suggesting that I should downgrade gnome-settings-daemon from 3.2.2-0ubuntu6 to 3.2.2-0ubuntu2.1? Or was that just an example of you showing that dpkg would work even if the File file were completely deleted?
**No** - simply showing you the difference in dpkg when the is a ../triggers/File & when there isn't. 
(g-s-d happened to be a .deb I had sitting on the desktop

dpkg will work without the "File" file but no "Processing triggers .."

If I had the same situation as you, (a corrupted File) then I'd go ahead like this. 

First get the contents of a good "File", FO has posted one for 10.10, might as well give it a try

```
gksudo gedit /var/lib/dpkg/triggers/File
``` 
Simply replace the contents with what he has posted in the code box for 10.10

(once gedit is open copy FO's code box, put focus back on gedit & go - 
Ctrl+a then Ctrl+v

---

### Post by Roger Allott on 2012-01-05
Right, I first off deleted the file named File. I then ran Update Manager, but now I had a different error message:
```
installArchives() failed: (Reading database ... 

dpkg: warning: files list file for package `akirad-keyring-and-mirrors' missing, assuming package has no files currently installed.
```
and no packages got updated.

Now, that error message gives me the heebeegeebees, because I had a hell of a problem about 9 months ago with the akirad repository simply refusing to die. [See this thread for the saga.]("http://ubuntuforums.org/showthread.php?t=1703618&highlight=akirad")

This is the first time though since that thread that akirad has reared its ugly head on me.

So, the next thing I did was create a new file with the text that FO had posted called File and saved it into the /var/lib/dpkg/triggers/ folder.

I then ran Update Manager but sadly I got exactly the same error message as above. I still can't install or update any packages.

---

### Post by Roger Allott on 2012-01-05
On a hunch, I popped into Synaptic and searched for "akirad".

To my surprise, there is indeed a package named akirad-keyring-and-mirrors and it showed up as being installed. So I selected to completely remove it and of course, because I have this error on dpkg, it failed!

I got the error message that I've added as an attachment image.

---

### Post by Roger Allott on 2012-01-05
I think what I need to do is to find any file in my filesystem that contains the text "akirad". And then I can zap whatever line on which it's mentioned.

I know that the command "locate akirad" searches for any file who's name includes that text, but what command looks at the contents of files and reports back which ones contain a certain text string?



**EDIT:** a bit of googling found my answer. It would seem that this command should do the trick:
```
grep -H -r akirad /
```
Although because it's rather pointless getting it to look at the /media folder, for example, I'm going through the root folders one at a time. It's taking a fair while to read through each of the files!

---

