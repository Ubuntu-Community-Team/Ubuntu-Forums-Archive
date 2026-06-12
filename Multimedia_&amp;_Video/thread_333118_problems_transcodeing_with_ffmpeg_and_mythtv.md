---
title: "problems transcodeing with ffmpeg and mythtv"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by dpsleep on 2007-01-06
so i have shows recorded with mythtv in the nuv formatt and am trying to convert them to flv (flash video) with ffmpeg. it works for the video, but not for the sound. when i run in term i get, 
```
$ ffmpeg -y -i /video/1008_20070106193600.nuv -r 20 -s 480x480 -deinterlace -ar 22050 /video/1008_20070106193600.nuv.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)

Seems that stream 0 comes from film source: 1000.00 (1000/1) -> 0.03 (100/2997)
Input #0, nuv, from '/video/1008_20070106193600.nuv':
  Duration: 00:01:10.2, start: 0.000000, bitrate: 1411 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 480x480,  0.03 fps(r)
  Stream #0.1: Audio: mp3, 32000 Hz, stereo, 1411 kb/s
Output #0, flv, to '/video/1008_20070106193600.nuv.flv':
  Stream #0.0: Video: flv, yuv420p, 480x480, q=2-31, 200 kb/s, 20.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
Marker bit missing before time_increment_resolutione= 382.5kbits/s    
[mpeg4 @ 0xb7e54ba8]time_base.den==0
[mpeg4 @ 0xb7e54ba8]header damaged
Error while decoding stream #0.0
Floating point exception (core dumped)

```

does anyone a with more knowledge about transcoding and ffmpeg know what is going on here?

---

### Post by tagra123 on 2007-01-06
> **dpsleep said:**
> so i have shows recorded with mythtv in the nuv formatt and am trying to convert them to flv (flash video) with ffmpeg. it works for the video, but not for the sound. when i run in term i get, 
```
$ ffmpeg -y -i /video/1008_20070106193600.nuv -r 20 -s 480x480 -deinterlace -ar 22050 /video/1008_20070106193600.nuv.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)

Seems that stream 0 comes from film source: 1000.00 (1000/1) -> 0.03 (100/2997)
Input #0, nuv, from '/video/1008_20070106193600.nuv':
  Duration: 00:01:10.2, start: 0.000000, bitrate: 1411 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 480x480,  0.03 fps(r)
  Stream #0.1: Audio: mp3, 32000 Hz, stereo, 1411 kb/s
Output #0, flv, to '/video/1008_20070106193600.nuv.flv':
  Stream #0.0: Video: flv, yuv420p, 480x480, q=2-31, 200 kb/s, 20.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
Marker bit missing before time_increment_resolutione= 382.5kbits/s    
[mpeg4 @ 0xb7e54ba8]time_base.den==0
[mpeg4 @ 0xb7e54ba8]header damaged
Error while decoding stream #0.0
Floating point exception (core dumped)

```

does anyone a with more knowledge about transcoding and ffmpeg know what is going on here?

Have you tried nuvexport.  I dont use flash but occasionally transcode to asf using the program. Most of the tim I transcode to dvd using nuvexport.

It was a small time sink getting it installed -- nothing like mythtv itself though.

---

### Post by dpsleep on 2007-01-07
> **tagra123 said:**
> Have you tried nuvexport.  I dont use flash but occasionally transcode to asf using the program. Most of the tim I transcode to dvd using nuvexport.

It was a small time sink getting it installed -- nothing like mythtv itself though.

well, i haven't tried nuvexport, but upon researching it i found out that the ubuntu default ffmpeg package doesnt come with mp3 exporting, so i need to build from source.... fun. but thanks for suggesting nuvexport, looks good.

---

### Post by dpsleep on 2007-01-07
ok, well i have it exporting mp3 now, but that apparently wasn't what was going wrong... still have the same error...

---

### Post by michwill on 2007-05-11
Anyone ever make any progress on this. . .?

---

### Post by michwill on 2007-05-14
Just FYI, mythburn.log shows the following when trying to use mytharchive to encode video.

```
mythburn.py (0.1.20061201-1) starting up...
Process priority 8
script path:/usr/share/mythtv/mytharchive/scripts
myth share path:/usr/share/mythtv
passed job file: /tmp/config/mydata.xml
passed progress log file: /tmp/logs/progress.log
mythburn.py (0.1.20061201-1) starting up...
Found 1 CPUs
Obtaining MythTV settings from MySQL database for hostname mythtv-desktop
Processing Mythburn job number 1.
Options - mediatype = 2, doburn = 1, createiso = 0, erasedvdrw = 1
          savefilename = ''
Looking for: /usr/share/mythtv/mytharchive/themes/G.A.N.T./theme.xml
Loading font 0, /usr/share/mythtv/FreeSans.ttf size 19
Loading font 1, /usr/share/mythtv/FreeSans.ttf size 15
Loading font 2, /usr/share/mythtv/FreeSans.ttf size 14
wantIntro: 1, wantMainMenu: 1, wantChapterMenu:1, wantDetailsPage: 1
Final DVD Video format will be ntsc
There are 1 files to process
Pre-processing file '1007_20070508233000.nuv' of type 'recording'
          Seinfeld
2007-05-14 12:00:20.320 Opening /var/lib/mythtv/recordings/1007_20070508233000.nuv
Input #0, nuv, from '/var/lib/mythtv/recordings/1007_20070508233000.nuv':
  Duration: 00:38:18.6, start: 0.000000, bitrate: 1411 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 480x480,  0.03 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 1411 kb/s
0: start_time: 0.000 duration: 2.299
1: start_time: 0.000 duration: 2.299
stream: start_time: 0.000 duration: 2298.694 bitrate=1411 kb/s
2007-05-14 12:00:20.346 duration = 2298
streaminfo.xml :-
<?xml version="1.0" ?>
<!DOCTYPE FILEINFO>
<file duration="2298" filename="/var/lib/mythtv/recordings/1007_20070508233000.nuv" type="nuv">    
        <streams count="2">        
                <video aspectratio="1.33333" bitrate="0" codec="mpeg4" ffmpegindex="0" fps="0.0333667" height="480" id="0" streamindex="0" width="480"/>        
                <audio bitrate="1411200" channels="2" codec="mp3" ffmpegindex="1" id="1" language="N/A" samplerate="48000" streamindex="1"/>        
        </streams>    
</file>
Video resolution is 480 by 480
*************************************************************
Processing file 1007_20070508233000.nuv of type recording
*************************************************************
File type is 'nuv'
Video codec is 'mpeg4'
2007-05-14 12:00:20.680 Opening /var/lib/mythtv/recordings/1007_20070508233000.nuv
Input #0, nuv, from '/var/lib/mythtv/recordings/1007_20070508233000.nuv':
  Duration: 00:38:18.6, start: 0.000000, bitrate: 1411 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 480x480,  0.03 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 1411 kb/s
0: start_time: 0.000 duration: 2.299
1: start_time: 0.000 duration: 2.299
stream: start_time: 0.000 duration: 2298.694 bitrate=1411 kb/s
2007-05-14 12:00:20.686 duration = 2298
streaminfo.xml :-
<?xml version="1.0" ?>
<!DOCTYPE FILEINFO>
<file duration="2298" filename="/var/lib/mythtv/recordings/1007_20070508233000.nuv" type="nuv">    
        <streams count="2">        
                <video aspectratio="1.33333" bitrate="0" codec="mpeg4" ffmpegindex="0" fps="0.0333667" height="480" id="0" streamindex="0" width="480"/>        
                <audio bitrate="1411200" channels="2" codec="mp3" ffmpegindex="1" id="1" language="N/A" samplerate="48000" streamindex="1"/>        
        </streams>    
</file>
Preferred audio languages eng and eng
Video id: 0x0, Audio1: [1] 0x1 (MP3, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Aspect ratio is 4:3
Re-encoding audio and video from nuv file
Encoding profile (SP) found
mythtranscode started PID = 8759
Waiting for mythtranscode to create the fifos
2007-05-14 12:00:21.052 Using runtime prefix = /usr
2007-05-14 12:00:21.103 New DB connection, total: 1
2007-05-14 12:00:21.110 Enabled verbose msgs: important
2007-05-14 12:00:21.115 New DB connection, total: 2
2007-05-14 12:00:21.178 Using protocol version 31
2007-05-14 12:00:21.385 mythtranscode: 0% Completed @ 28.5714 fps.
Running ffmpeg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --libdir=${prefix}/lib --shlibdir=${prefix}/lib --incdir=${prefix}/include/ffmpeg --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir=${prefix}/share/man --enable-libvorbis --enable-pthreads --enable-libfaac --enable-xvid --enable-libdts --enable-amr_nb --enable-amr_wb --enable-pp --enable-libogg --enable-libgsm --enable-x264 --enable-liba52 --enable-libtheora --extra-cflags=-Wall -g -fPIC -DPIC --cc=ccache cc --enable-swscaler
  libavutil version: 49.4.0
  libavcodec version: 51.40.2
  libavformat version: 51.11.0
  built on Mar 29 2007 11:08:52, gcc: 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)
Input #0, s16le, from '/tmp/work/1/audout':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Input #1, rawvideo, from '/tmp/work/1/vidout':
  Duration: N/A, bitrate: N/A
  Stream #1.0: Video: rawvideo, yuv420p, 480x480,  0.03 fps(r)
Output #0, dvd, to '/tmp/work/1/newfile2.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, q=5-31, 4771 kb/s,  5.00 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
[mpeg2video @ 0xb7d83808]MPEG1/2 does not support 5/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
************************************************************
ERROR: Failed while running ffmpeg to re-encode video.
Command was /usr/bin/ffmpeg -y -f s16le -ar 48000 -ac 2 -i /tmp/work/1/audout -f rawvideo -pix_fmt yuv420p -s 480x480 -aspect 1.33333 -r 0.0333667 -i /tmp/work/1/vidout -aspect 1.33333 -r 0.0333667 -s 720x480 -b 4771k -vcodec mpeg2video -qmin 5 -ab 192 -ar 48000 -acodec ac3 -f dvd "/tmp/work/1/newfile2.mpg"
************************************************************

chmod: changing permissions of `/tmp': Operation not permitted
chmod: changing permissions of `/tmp/.ICE-unix': Operation not permitted
chmod: changing permissions of `/tmp/gconfd-root': Operation not permitted
chmod: `/tmp/gconfd-root': Permission denied
chmod: changing permissions of `/tmp/.X0-lock': Operation not permitted
chmod: changing permissions of `/tmp/orbit-root': Operation not permitted
chmod: `/tmp/orbit-root': Permission denied
chmod: changing permissions of `/tmp/gedit.root.1740485529': Operation not permitted
chmod: changing permissions of `/tmp/.X11-unix': Operation not permitted
chmod: changing permissions of `/tmp/.X11-unix/X0': Operation not permitted
Terminated
```

---

