---
title: "DVDStyler issue."
date: 2015-08-04
forum: Multimedia Software
---

### Post by 77_GCSX on 2015-08-04
I am trying to convert/make a DVD from 6 mp4 files.

As soon as I get the "Transcode/remultiplex" msg the log below starts filling up with this one recurring error:

"libavfilter does not support this channel layout"

I have, in the past, used DVDStyler with mpg2 files with no issues so, is this because I am using mp4's?

Here is an excerpt from the log of DVDStyler:

```
DVDStyler v2.5.2
Linux 3.13.0-61-generic x86_64
Libav: libavformat 54.20.3, libavcodec 54.35.0, libavutil 52.3.0
Prepare
Cleaning temporary directory
Search for transcoded files in cache
Generating menus
Generating menu 1 of 2
Create menu MPEG
Multiplexing subpictures into mpeg
Menu has 1 group(s) of changeable colours.
Executing command: spumux -P -s 0 "/tmp/dvd-tmp/menu1-0.mpg_spumux.xml"
DVDAuthor::spumux, version 0.7.0.
Build options: gnugetopt imagemagick iconv freetype fribidi fontconfig
Send bug reports to <dvdauthor-users@lists.sourceforge.net>
INFO: no default video format, must explicitly specify NTSC or PAL
INFO: Picture /tmp/dvd-tmp/menu1-0.mpg_buttons.png had 1 colors
INFO: Picture /tmp/dvd-tmp/menu1-0.mpg_highlight.png had 4 colors
INFO: Picture /tmp/dvd-tmp/menu1-0.mpg_select.png had 4 colors
INFO: Pickbuttongroups, success with 1 groups, useimg=1
INFO: 0 bytes of data written
INFO: 6144 bytes of data written
INFO: 12288 bytes of data written
INFO: 16384 bytes of data written
INFO: 22528 bytes of data written
INFO: Found EOF in .sub file.
INFO: Max_sub_size=98
INFO: 28672 bytes of data written
INFO: 1 subtitles added, 0 subtitles skipped, stream: 32, offset: 1.00
Generating menu 2 of 2
Create menu MPEG
Multiplexing subpictures into mpeg
Menu has 2 group(s) of changeable colours.
Executing command: spumux -P -s 0 "/tmp/dvd-tmp/menu1-1.mpg_spumux.xml"
DVDAuthor::spumux, version 0.7.0.
Build options: gnugetopt imagemagick iconv freetype fribidi fontconfig
Send bug reports to <dvdauthor-users@lists.sourceforge.net>
INFO: no default video format, must explicitly specify NTSC or PAL
INFO: Picture /tmp/dvd-tmp/menu1-1.mpg_buttons.png had 1 colors
INFO: Picture /tmp/dvd-tmp/menu1-1.mpg_highlight.png had 4 colors
INFO: Picture /tmp/dvd-tmp/menu1-1.mpg_select.png had 5 colors
INFO: Pickbuttongroups, success with 2 groups, useimg=1
INFO: 0 bytes of data written
INFO: 18432 bytes of data written
INFO: 36864 bytes of data written
INFO: 55296 bytes of data written
INFO: 73728 bytes of data written
INFO: Found EOF in .sub file.
INFO: Max_sub_size=3952
INFO: 1 subtitles added, 0 subtitles skipped, stream: 32, offset: 1.00
Transcode/remultiplex
Add file to cache:/tmp/dvd-cache/entry001.vob
Transcode video file: /home/paul1/Videos/Katrina Movies/MP4's/01_Halloweentown.mp4
Need encode: true, use mplex: false
Executing command: avconv -i "/home/paul1/Videos/Katrina Movies/MP4's/01_Halloweentown.mp4" -f dvd -c:v:0 mpeg2video -s 720x480 -r 24000/1001 -g 18 -b:v:0 799000 -maxrate:v:0 799000 -minrate:v:0 799000 -bufsize:v:0 1835008 -packetsize 2048 -muxrate 10080000 -b:a 192000 -ar 48000 -c:a:0 ac3 -map 0:v -map 0:a "/tmp/dvd-cache/entry001.vob"
ffmpeg version 1.2.6-7:1.2.6-1~trusty1 Copyright (c) 2000-2014 the FFmpeg developers
  built on Apr 26 2014 18:52:58 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --arch=amd64 --disable-stripping --enable-avresample --enable-pthreads --enable-runtime-cpudetect --extra-version='7:1.2.6-1~trusty1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  avcodec     configuration: --prefix=/usr --extra-cflags='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security ' --extra-ldflags='-Wl,-z,relro' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-nonfree --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-libvpx --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-librtmp --enable-avfilter --enable-libfreetype --enable-libvo-aacenc --disable-decoder=amrnb --enable-libvo-amrwbenc --enable-libaacplus --libdir=/usr/lib/x86_64-linux-gnu --disable-vda --enable-libbluray --enable-libcdio --enable-gnutls --enable-frei0r --enable-openssl --enable-libass --enable-libopus --enable-fontconfig --enable-libfdk-aac --enable-libdc1394 --disable-a  avformat    configuration: --prefix=/usr --extra-cflags='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security ' --extra-ldflags='-Wl,-z,relro' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-nonfree --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-libvpx --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-librtmp --enable-avfilter --enable-libfreetype --enable-libvo-aacenc --disable-decoder=amrnb --enable-libvo-amrwbenc --enable-libaacplus --libdir=/usr/lib/x86_64-linux-gnu --disable-vda --enable-libbluray --enable-libcdio --enable-gnutls --enable-frei0r --enable-openssl --enable-libass --enable-libopus --enable-fontconfig --enable-libfdk-aac --enable-libdc1394 --disable-a  swscale     configuration: --prefix=/usr --extra-cflags='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security ' --extra-ldflags='-Wl,-z,relro' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-nonfree --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-libvpx --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-librtmp --enable-avfilter --enable-libfreetype --enable-libvo-aacenc --disable-decoder=amrnb --enable-libvo-amrwbenc --enable-libaacplus --libdir=/usr/lib/x86_64-linux-gnu --disable-vda --enable-libbluray --enable-libcdio --enable-gnutls --enable-frei0r --enable-openssl --enable-libass --enable-libopus --enable-fontconfig --enable-libfdk-aac --enable-libdc1394 --disable-a  swresample  configuration: --prefix=/usr --extra-cflags='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security ' --extra-ldflags='-Wl,-z,relro' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-nonfree --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-libvpx --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-librtmp --enable-avfilter --enable-libfreetype --enable-libvo-aacenc --disable-decoder=amrnb --enable-libvo-amrwbenc --enable-libaacplus --libdir=/usr/lib/x86_64-linux-gnu --disable-vda --enable-libbluray --enable-libcdio --enable-gnutls --enable-frei0r --enable-openssl --enable-libass --enable-libopus --enable-fontconfig --enable-libfdk-aac --enable-libdc1394 --disable-a  postproc    configuration: --prefix=/usr --extra-cflags='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security ' --extra-ldflags='-Wl,-z,relro' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-nonfree --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-libvpx --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-librtmp --enable-avfilter --enable-libfreetype --enable-libvo-aacenc --disable-decoder=amrnb --enable-libvo-amrwbenc --enable-libaacplus --libdir=/usr/lib/x86_64-linux-gnu --disable-vda --enable-libbluray --enable-libcdio --enable-gnutls --enable-frei0r --enable-openssl --enable-libass --enable-libopus --enable-fontconfig --enable-libfdk-aac --enable-libdc1394 --disable-a  libavutil      52. 18.100 / 52. 18.100
  libavcodec     54. 92.100 / 54. 59.100
  libavformat    54. 63.104 / 54. 29.104
  libavdevice    53.  5.103 / 53.  5.103
  libavfilter     3. 42.103 /  3. 42.103
  libswscale      2.  2.100 /  2.  1.101
  libswresample   0. 17.102 /  0. 15.100
  libpostproc    52.  2.100 / 52.  0.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/paul1/Videos/Katrina Movies/MP4's/01_Halloweentown.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    creation_time   : 2015-08-03 15:04:11
    title           : halloweentown_xvid
    artist          : Duwayne Dunham
    encoder         : HandBrake 0.10.2 2015061000
    comment         : Captions: 
                    : English
    genre           : Family
  Duration: 01:24:18.97, start: 0.000000, bitrate: 902 kb/s
    Stream #0:0(und): Video: h264 (Main) (avc1 / 0x31637661), yuv420p, 512x384 [SAR 1:1 DAR 4:3], 734 kb/s, 23.98 fps, 23.98 tbr, 90k tbn, 180k tbc
    Metadata:
      creation_time   : 2015-08-03 15:04:11
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: aac (mp4a / 0x6134706D), 48000 Hz, stereo, s16, 160 kb/s
    Metadata:
      creation_time   : 2015-08-03 15:04:11
      handler_name    : Stereo
[mpeg2video @ 0x20a0fa0] Warning vbv_delay will be set to 0xFFFF (=VBR) as the specified vbv buffer is too large for the given bitrate!
Output #0, dvd, to '/tmp/dvd-cache/entry001.vob':
  Metadata:
    major_brand     : mp42
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    genre           : Family
    title           : halloweentown_xvid
    artist          : Duwayne Dunham
    comment         : Captions: 
                    : English
    encoder         : Lavf54.29.104
    Stream #0:0(und): Video: mpeg2video, yuv420p, 720x480 [SAR 8:9 DAR 4:3], q=2-31, 799 kb/s, 90k tbn, 23.98 tbc
    Metadata:
      creation_time   : 2015-08-03 15:04:11
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: ac3, 48000 Hz, stereo, flt, 192 kb/s
    Metadata:
      creation_time   : 2015-08-03 15:04:11
      handler_name    : Stereo
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> mpeg2video)
  Stream #0:1 -> #0:1 (aac -> ac3)
Press [q] to stop, [?] for help
libavfilter does not support this channel layout
    Last message repeated 313 times
frame=  153 fps=0.0 q=1.6 size=       0kB time=00:00:06.29 bitrate=   0.0kbits/s    
libavfilter does not support this channel layout
    Last message repeated 277 times
frame=  295 fps=295 q=4.6 size=       0kB time=00:00:12.22 bitrate=   0.0kbits/s    
libavfilter does not support this channel layout
    Last message repeated 273 times
frame=  435 fps=290 q=8.3 size=       0kB time=00:00:18.05 bitrate=   0.0kbits/s    
libavfilter does not support this channel layout
    Last message repeated 280 times
frame=  579 fps=289 q=9.5 size=       0kB time=00:00:24.06 bitrate=   0.0kbits/s    
libavfilter does not support this channel layout
    Last message repeated 281 times
frame=  723 fps=289 q=4.9 size=       0kB time=00:00:30.07 bitrate=   0.0kbits/s    
libavfilter does not support this channel layout
Aborted
```



I am running Ubuntu 14.04 LTS.

If you need any more info just ask.

Thanks, Paul

---

### Post by mc4man on 2015-08-04
using .mp4 in dvdstyler is not an issue here. Maybe because dvdstyler was built to use avconv & you're substituting ffmpeg from Jon Severinsson's old trusty ppa (ppa no longer exists..

---

### Post by 77_GCSX on 2015-08-05
Can I install avconv along side ffmpeg? Or is there another way to have Styler use avconv?

Thanks!

---

### Post by mc4man on 2015-08-05
dvdstyler depends on avconv (libav-tools) so it's installed. I've no idea how those ffmpeg builds worked or *really if it is your actual issue.* Just a possibility as your log shows  - 
> Executing command: avconv -i "/home/paul1/Videos/Katrina Movies/MP4's/01_Halloweentown.mp4" -f dvd -c:v:0 mpeg2video -s 720x480 -r 24000/1001 -g 18 -b:v:0 799000 -maxrate:v:0 799000 -minrate:v:0 799000 -bufsize:v:0 1835008 -packetsize 2048 -muxrate 10080000 -b:a 192000 -ar 48000 -c:a:0 ac3 -map 0:v -map 0:a "/tmp/dvd-cache/entry001.vob"
ffmpeg version 1.2.6-7:1.2.6-1~trusty1 Copyright (c) 2000-2014 the FFmpeg developers

What do these show?
```
apt-cache policy ffmpeg libav-tools
```
```
apt-cache show ffmpeg
```

---

### Post by 77_GCSX on 2015-08-07
> **mc4man said:**
> dvdstyler depends on avconv (libav-tools) so it's installed. I've no idea how those ffmpeg builds worked or *really if it is your actual issue.* Just a possibility as your log shows  - 


What do these show?
```
apt-cache policy ffmpeg libav-tools
```

ffmpeg:
  Installed: 7:1.2.6-1~trusty1
  Candidate: 7:1.2.6-1~trusty1
  Version table:
 *** 7:1.2.6-1~trusty1 0
        100 /var/lib/dpkg/status
libav-tools:
  Installed: 7:1.2.6-1~trusty1
  Candidate: 7:1.2.6-1~trusty1
  Version table:
 *** 7:1.2.6-1~trusty1 0
        100 /var/lib/dpkg/status
     6:9.18-0ubuntu0.14.04.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security/universe amd64 Packages
     6:9.11-2ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages

```
apt-cache show ffmpeg
```

Package: ffmpeg
Status: install ok installed
Priority: optional
Section: video
Installed-Size: 833
Maintainer: Jon Severinsson <jon@severinsson.net>
Architecture: amd64
Version: 7:1.2.6-1~trusty1
Replaces: libav-tools (<< 7:0.10~), libavcodec-extra-52 (<< 4:0.6~), libavcodec52 (<< 4:0.6-2~)
Depends: libavcodec54 (>= 7:1.2.5~) | libavcodec-extra-54 (>= 7:1.2.5~), libavdevice53 (>= 7:1.2.5~), libavfilter3 (>= 7:1.2.5~), libavformat54 (>= 7:1.2.5~), libavresample1 (>= 7:1.2.5~), libavutil52 (>= 7:1.2.5~), libc6 (>= 2.14), libpostproc52 (>= 7:1.2.5~), libsdl1.2debian (>= 1.2.11), libswresample0 (>= 7:1.2.5~), libswscale2 (>= 7:1.2.5~)
Pre-Depends: dpkg (>= 1.15.6~)
Suggests: frei0r-plugins
Breaks: libav-tools (<< 7:0.10~)
Conflicts: ffprobe
Conffiles:
 /etc/ffserver.conf 58e16a2e25539de5e0fba8edfa46629a
Description: Multimedia player, server, encoder and transcoder
 FFmpeg is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This package contains the ffplay multimedia player, the ffserver
 streaming server, the ffmpeg audio and video encoder, and the ffprobe
 stream analyzer.  They support most existing file formats (AVI, MPEG,
 OGG, Matroska, ASF...) and encoding formats (MPEG, DivX, MPEG4, AC3,
 DV...). Additionally, it contains the qt-faststart utility which
 rearranges Quicktime files to facilitate network streaming.
Description-md5: 4022138915d83d761d1cb1f90f2cf45a
Homepage: [http://ffmpeg.org/](http://ffmpeg.org/)
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>


I've done some further testing. With Styler I can convert an 87mb mpg2 file in a short amount of time. However, using Styler, DevedeNG or Bombono, when try to make a DVD with 7 mp4's, sizes ranging from 490mb to 1.3gb, I let my PC run the DVD authoring for 9+ hours and I STILL have no output. When I logged on the my PC to check the status there had been no change in how far it had gotten with regards to actually finishing the author.

My PC specs (if it helps) are:

Intel® Core™ i7 CPU 870 @ 2.93GHz × 8 with DDR3 1333 8gb ram.

I'm just starting to pull my hair out on this so any help is GREATLY appreciated. :)

Thanks, Paul

---

### Post by mc4man on 2015-08-07
It appears that the ppa has installed ffmpeg shared libs that either avconv is using or the avconv command/binary is being diverted to ffmpeg
What does simply avconv in a terminal show?
(ex. here on my trusty, your version would be lower but otherwise the same (no mention of ffmpeg...
> ~$ avconv
avconv version 11.1-6:11.1-1~ppa, Copyright (c) 2000-2014 the Libav developers
  built on Jan  1 2015 23:58:18 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
Hyper fast Audio and Video encoder
usage: avconv [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man avconv'


You could consider - 
installing ppa-purge & purging the ppa. That would return you back to default 14.04 libs. This would require the ppa still being enabled in your sources, if it isn't still enabled you may be out of luck with ppa-purge as you can't re-add the ppa

If the above isn't suitable or can't work then you can either - 
remove ffmpeg & all the ppa shared libs, then re-install using the trusty packages, could be a pita as you'll lose alot

If sticking with 14.04 consider upgrading the whole mess, I've 2 ppa's that if used together may do that fine, could be tested with a simple simulation first.

---

### Post by 77_GCSX on 2015-08-07
~$ avconv
ffmpeg version 1.2.6-7:1.2.6-1~trusty1 Copyright (c) 2000-2014 the FFmpeg developers
  built on Apr 26 2014 18:52:58 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --arch=amd64 --disable-stripping --enable-avresample --enable-pthreads --enable-runtime-cpudetect --extra-version='7:1.2.6-1~trusty1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  avcodec     configuration: --prefix=/usr --extra-cflags='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security ' --extra-ldflags='-Wl,-z,relro' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-nonfree --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-libvpx --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-librtmp --enable-avfilter --enable-libfreetype --enable-libvo-aacenc --disable-decoder=amrnb --enable-libvo-amrwbenc --enable-libaacplus --libdir=/usr/lib/x86_64-linux-gnu --disable-vda --enable-libbluray --enable-libcdio --enable-gnutls --enable-frei0r --enable-openssl --enable-libass --enable-libopus --enable-fontconfig --enable-libfdk-aac --enable-libdc1394 --disable-a  avformat    configuration: --prefix=/usr --extra-cflags='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security ' --extra-ldflags='-Wl,-z,relro' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-nonfree --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-libvpx --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-librtmp --enable-avfilter --enable-libfreetype --enable-libvo-aacenc --disable-decoder=amrnb --enable-libvo-amrwbenc --enable-libaacplus --libdir=/usr/lib/x86_64-linux-gnu --disable-vda --enable-libbluray --enable-libcdio --enable-gnutls --enable-frei0r --enable-openssl --enable-libass --enable-libopus --enable-fontconfig --enable-libfdk-aac --enable-libdc1394 --disable-a  swscale     configuration: --prefix=/usr --extra-cflags='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security ' --extra-ldflags='-Wl,-z,relro' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-nonfree --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-libvpx --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-librtmp --enable-avfilter --enable-libfreetype --enable-libvo-aacenc --disable-decoder=amrnb --enable-libvo-amrwbenc --enable-libaacplus --libdir=/usr/lib/x86_64-linux-gnu --disable-vda --enable-libbluray --enable-libcdio --enable-gnutls --enable-frei0r --enable-openssl --enable-libass --enable-libopus --enable-fontconfig --enable-libfdk-aac --enable-libdc1394 --disable-a  swresample  configuration: --prefix=/usr --extra-cflags='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security ' --extra-ldflags='-Wl,-z,relro' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-nonfree --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-libvpx --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-librtmp --enable-avfilter --enable-libfreetype --enable-libvo-aacenc --disable-decoder=amrnb --enable-libvo-amrwbenc --enable-libaacplus --libdir=/usr/lib/x86_64-linux-gnu --disable-vda --enable-libbluray --enable-libcdio --enable-gnutls --enable-frei0r --enable-openssl --enable-libass --enable-libopus --enable-fontconfig --enable-libfdk-aac --enable-libdc1394 --disable-a  postproc    configuration: --prefix=/usr --extra-cflags='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security ' --extra-ldflags='-Wl,-z,relro' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-nonfree --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-libvpx --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-librtmp --enable-avfilter --enable-libfreetype --enable-libvo-aacenc --disable-decoder=amrnb --enable-libvo-amrwbenc --enable-libaacplus --libdir=/usr/lib/x86_64-linux-gnu --disable-vda --enable-libbluray --enable-libcdio --enable-gnutls --enable-frei0r --enable-openssl --enable-libass --enable-libopus --enable-fontconfig --enable-libfdk-aac --enable-libdc1394 --disable-a  libavutil      52. 18.100 / 52. 18.100
  libavcodec     54. 92.100 / 54. 59.100
  libavformat    54. 63.104 / 54. 29.104
  libavdevice    53.  5.103 / 53.  5.103
  libavfilter     3. 42.103 /  3. 42.103
  libswscale      2.  2.100 /  2.  1.101
  libswresample   0. 17.102 /  0. 15.100
  libpostproc    52.  2.100 / 52.  0.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'

That's the output from avconv. Seems to be A LOT more than yours.

The weird thing about this whole deal is the only change I have made to my system was a switch to this Intel® Core™ i7 CPU 870. The other PC was an older HP, so I was hoping the switch would speed things up. It's not like I'm doing anything out of the ordinary. I'm just adding mp4's to a DVD project.

I await your command..lol!

Thanks, Paul

BTW: I have tried Bombono and when I add an MP4 to a project the window turns gray and then Bombono crashes.

---

### Post by mc4man on 2015-08-07
So that ppa diverts avconv to ffmpeg. 
Because the ppa was removed not too sure there is any advantage to using what it provided.
You could try - 
```
sudo apt-get install ppa-purge
```
when done - 
```
sudo ppa-purge ppa:jon-severinsson/ffmpeg
```
It'll either work, report it cannot find package list for ppa or semi-work. (you'll likely only get one chance at this as ppa-purge will disable the ppa if enabled.

If it seems to semi-work then copy & post complete terminal output & don't log out or restart yet..
If it doesn't work at all we can test something else.

---

### Post by 77_GCSX on 2015-08-07
Good to hear and a BIG Thanks for the terminal commands. It might be a few days but I'll be getting to it.

Thanks again!
Paul

---

### Post by gordintoronto on 2015-08-08
In the past, I have found devede excellent for what you are doing. It has a wonderful help file. Note that it produces an iso, and you use Brasero or K3B to burn the image to DVD.

---

### Post by 77_GCSX on 2015-08-09
> **mc4man said:**
> So that ppa diverts avconv to ffmpeg. 
Because the ppa was removed not too sure there is any advantage to using what it provided.
You could try - 
```
sudo apt-get install ppa-purge
```
when done - 
```
sudo ppa-purge ppa:jon-severinsson/ffmpeg
```
It'll either work, report it cannot find package list for ppa or semi-work. (you'll likely only get one chance at this as ppa-purge will disable the ppa if enabled.

If it seems to semi-work then copy & post complete terminal output & don't log out or restart yet..
If it doesn't work at all we can test something else.

Ok, I did the apt-get and the purge of jon-severinson and here is the Terminal output:

~$ sudo ppa-purge ppa:jon-severinsson/ffmpeg
Updating packages lists
PPA to be removed: jon-severinsson ffmpeg
Warning:  Could not find package list for PPA: jon-severinsson ffmpeg

I JUST did this and now I'm going to try Styler even though this 'appears' to have not done anything. I'll be reporting back shortly.

Just fired up Styler and I'm getting the same msg 'libavfilter does not support this channel layout'. I did NOT get that with the Styler on the older PC.

I'd wait until the whole movie was done but I have to leave for work at 2p and I know this will take longer than that.

Also, I could post the log from Styler if it would help. It's quite lengthy so just let me know if you'd like to see that and I'll post it.

---

### Post by mc4man on 2015-08-09
> Warning: Could not find package list for PPA: jon-severinsson ffmpeg
Well the ppa was either disabled previously or got the name wrong (can't directly check as the ppa was removed, can't understand why someone would do that, if you're done with it just leave & forget.

Maybe this will show something useful - 
```
ls  /etc/apt/sources.list.d
```

---

### Post by 77_GCSX on 2015-08-09
> **mc4man said:**
> 
Maybe this will show something useful - 
```
ls  /etc/apt/sources.list.d
```

Last thing before I leave for work:

~$ ls  /etc/apt/sources.list.d
deb-multimedia.list
deb-multimedia.list.save
getdeb.list
getdeb.list.save
gnome3-team-gnome3-trusty.list
gnome3-team-gnome3-trusty.list.save
google-talkplugin.list
google-talkplugin.list.save
jon-severinsson-ffmpeg-trusty.list
jon-severinsson-ffmpeg-trusty.list.save
libdvdcss.list
libdvdcss.list.save
noobslab-apps-trusty.list
noobslab-apps-trusty.list.save
noobslab-themes-trusty.list
noobslab-themes-trusty.list.save
otto-kesselgulasch-gimp-trusty.list
otto-kesselgulasch-gimp-trusty.list.save
playdeb.list
playdeb.list.save
playonlinux.list
playonlinux.list.save
plex.list
plex.list.save
stebbins-handbrake-releases-trusty.list
stebbins-handbrake-releases-trusty.list.save
stedy6-stedy-minidna-trusty.list
stedy6-stedy-minidna-trusty.list.save
thefanclub-grive-tools-trusty.list
thefanclub-grive-tools-trusty.list.save
tualatrix-ppa-trusty.list
tualatrix-ppa-trusty.list.save
ubuntu-clamav-ppa-trusty.list
ubuntu-clamav-ppa-trusty.list.save
ubuntuhandbook1-dvdstyler-trusty.list
ubuntuhandbook1-dvdstyler-trusty.list.save
ubuntu-wine-ppa-trusty.list
ubuntu-wine-ppa-trusty.list.save
videolan-stable-daily-trusty.list
videolan-stable-daily-trusty.list.save
webupd8team-java-trusty.list
webupd8team-java-trusty.list.save
webupd8team-y-ppa-manager-trusty.list
webupd8team-y-ppa-manager-trusty.list.save
xorg-edgers-ppa-trusty.list
xorg-edgers-ppa-trusty.list.save

I checked Software and Updates and noticed that the one we're working in is NOT checked off.

---

### Post by mc4man on 2015-08-09
i guess you no longer have a package list for that ppa & there is no way to refresh since it's gone.
With that list of ppa's I'd be hesitant to suggest adding 2 more that could resolve (would give you major updates to numerous packages.

If you installed or have synaptic package manager does it show the ffmpeg ppa in the Origins tab? ex. in screen

---

### Post by FakeOutdoorsman on 2015-08-10
> **mc4man said:**
> Well the ppa was either disabled previously or got the name wrong (can't directly check as the ppa was removed, can't understand why someone would do that, if you're done with it just leave & forget.

I never figured out why that PPA was "discontinued". Who knows how long it was listed on FFmpeg download page before users started mentioning it was missing.

---

### Post by 77_GCSX on 2015-08-10
> **mc4man said:**
> i guess you no longer have a package list for that ppa & there is no way to refresh since it's gone.
With that list of ppa's I'd be hesitant to suggest adding 2 more that could resolve (would give you major updates to numerous packages.

If you installed or have synaptic package manager does it show the ffmpeg ppa in the Origins tab? ex. in screen

Right there at the top.

---

### Post by mc4man on 2015-08-10
> **77_GCSX said:**
> Right there at the top.

No, what I meant was there 1 or 2 listings for that particular ppa below "All", generally you get 2 for each ppa, one shows all that are currently  installed from that ppa, (/now), the 2nd one all that is available from that ppa, (/trusty). If you scroll down that list is there any thing for the seversion ppa. (at best there would be one for 
(- you can pull the the vertical divider for that column to the right if desired to see full names.

If not then you'll need to remove all the ffmpeg related packages that have 7:1.2.6-1~trusty1 version in the package name, ie, - red not sure of number
libavcodec54 or libavcodec-extra-54 
libavdevice53 
libavfilter3 
libavformat54
libavresample1
libavutil52
libpostproc52 
libswresample[COLOR="#FF0000"]1[/COLOR]
libswscale2 

This is fairly easy if used to such activity, if not then you will be able to do this but may take a little or a little further help during. Note that this is 'non fatal' to your install, it's just multimedia packages.

To find them better don't use the quick filter in synaptic (make sure that it is empty), use the Search icon,  search ffmpeg.  You have to remove them **all,** it's probable that when you mark libavcodec54 or libavcodec-extra-54 for removal synaptic will try to mark the other for install. Just mark that one for removal also if it does.
It's also quite likely that synaptic will at some point pop up a 'you hold broken...' window, if so just close the pop up & click on the 'Reload' icon.

In addition to removing all these ffmpeg packages you'll also lose quite a number of other packages,  anything that depends on ffmpeg or it's libs will be removed. 

Once they are all removed then you'd click on the Reload button again, then start re-installing all the removed packages you want back. If at any point synaptic pops up the broken packages window, again close it, (the pop up) & reload. If something can't be marked (turns red) then close synaptic & try with apt-get from terminal to see why.

In synaptic's menu, File > History will give you a list of everything that was removed when getting rid of the ppa packages. (again you may need to pull that vertical divider to expose that column better

You should use a maximized synaptic for easier use.

If it seems too daunting then  - 
1. live with current 
2. do a fresh 14.04 install
3. - run this simulation, post complete terminal output. 

```
sudo apt-get -s purge libavcodec-extra-54 libavcodec54  libavdevice53 libavfilter3 libavformat54  libswscale2 libavutil52

```

---

### Post by 77_GCSX on 2015-08-11
I followed your instructions as far as removing and re-installing the packages.

So far so good (knock on wood) everything seems to be working again. I started with Styler and that all seems to work fine and Handbrake doesn't have any issues either.

I can't thank you enough for your patience and time!

Thanks, Paul

---

