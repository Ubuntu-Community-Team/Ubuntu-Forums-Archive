---
title: "Mytharchive Cannot choose 4:3 aspect ratio"
date: 2010-10-29
forum: Mythbuntu
---

### Post by eljeffe on 2010-10-29
I have several shows that I record using standard def, i.e. ntsc, input. Their native aspect ratio is 4:3. I record them at 720x480. 

When using mytharchive to create a dvd, the aspect ratio is forced to 16:9. I can change this in the internal dvd player, but when I put them in a standalone player the image is shortened. 

I have tried changing the settings for menu and or chapters in the mytharchive settings screens, hoping that they would influence the final aspect ratio of the DVD. None help. Is there somewhere else that I haven't found that will allow me to force 4:3 on the final ISO?

Thanks

---

### Post by eljeffe on 2010-10-29
More info

I have tried it on the ffmpeg command line, and also from the ffmpeg_dvd_ntsc.xml file. In neither place do I seem to be able to override this behavior.

It seems that the video is detected as 4:3 (DAR) but when it sets the output it changes to 16:9.

From the log (bold shows the two states):

```
Input #0, nuv, from '/var/lib/mythtv/recordings/1011_20101029003000.nuv':
  Duration: 10:15:43.64, start: 0.037000, bitrate: 127 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x480, PAR 8:9 DAR 4:3, 29.97 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 128 kb/s
2010-10-29 17:18:40.855 duration = 36943
2010-10-29 17:18:40.855 Extracting details from: 1011_20101029003000.nuv
2010-10-29 17:18:40.856 chanid: 1011 starttime:2010-10-29T00:30:00 
2010-10-29 17:18:40.857 File is a Myth recording.
2010-10-29 17:18:40.858 cutframes = 0
2010-10-29 17:18:40.858 cutduration = 0
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="36943" duration="36943" filename="/var/lib/mythtv/recordings/1011_20101029003000.nuv" type="nuv">    
        <streams count="2">        
                <video aspectratio="N/A" bitrate="0" codec="mpeg4" ffmpegindex="0" fps="29.97" height="480" id="0" start_time="0.88" streamindex="0" width="720"/>        
                <audio bitrate="128000" channels="2" codec="mp3" ffmpegindex="1" id="1" language="N/A" samplerate="48000" start_time="0.37" streamindex="1"/>        
        </streams>    
</file>
          The New Adventures of Old Christine
Video resolution is 720 by 480
*************************************************************
Processing recording 1: '/var/lib/mythtv/recordings/1011_20101029003000.nuv'
*************************************************************
2010-10-29 17:18:40.943 getFileInfo(): Opening '/var/lib/mythtv/recordings/1011_20101029003000.nuv'
[nuv @ 0xb117c0]Estimating duration from bitrate, this may be inaccurate
[B]Input #0, nuv, from '/var/lib/mythtv/recordings/1011_20101029003000.nuv':
  Duration: 10:15:43.64, start: 0.037000, bitrate: 127 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x480, PAR 8:9 DAR 4:3, 29.97 tbr, 1k tbn, 1k tbc[/B]
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 128 kb/s
2010-10-29 17:18:40.958 duration = 36943
2010-10-29 17:18:40.958 Extracting details from: 1011_20101029003000.nuv
2010-10-29 17:18:40.959 chanid: 1011 starttime:2010-10-29T00:30:00 
2010-10-29 17:18:40.961 File is a Myth recording.
2010-10-29 17:18:40.961 cutframes = 0
2010-10-29 17:18:40.961 cutduration = 0
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="36943" duration="36943" filename="/var/lib/mythtv/recordings/1011_20101029003000.nuv" type="nuv">    
        <streams count="2">        
                <video aspectratio="N/A" bitrate="0" codec="mpeg4" ffmpegindex="0" fps="29.97" height="480" id="0" start_time="0.88" streamindex="0" width="720"/>        
                <audio bitrate="128000" channels="2" codec="mp3" ffmpegindex="1" id="1" language="N/A" samplerate="48000" start_time="0.37" streamindex="1"/>        
        </streams>    
</file>
Preferred audio languages eng and eng
Video id: 0x0, Audio1: [1] 0x1 (MP3, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Re-encoding audio and video from nuv file
Using encoder profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd_ntsc.xml
Encoding profile (4:3 SP) found
mythtranscode started PID = 2230
Waiting for mythtranscode to create the fifos
2010-10-29 17:18:41.047 Using runtime prefix = /usr
2010-10-29 17:18:41.048 Using configuration directory = /home/jeff/.mythtv
2010-10-29 17:18:41.048 Empty LocalHostName.
2010-10-29 17:18:41.052 New DB connection, total: 1
2010-10-29 17:18:41.054 Closing DB connection named 'DBManager0'
2010-10-29 17:18:41.055 Enabled verbose msgs: important
2010-10-29 17:18:41.056 ProgramInfo(): Updated pathname '':'' -> '1011_20101029003000.nuv'
2010-10-29 17:18:41.186 mythtranscode: 0% Completed @ 90.9091 fps.
2010-10-29 17:18:41.194 Using protocol version 23056
Running ffmpeg
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
Input #0, s16le, from '/var/lib/mytharchive/temp/work/1/audout':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Input #1, rawvideo, from '/var/lib/mytharchive/temp/work/1/vidout':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #1.0: Video: rawvideo, yuv420p, 720x480, 29.97 tbr, 29.97 tbn, 29.97 tbc
[B]Output #0, dvd, to '/var/lib/mytharchive/temp/work/1/newfile2.mpg':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], q=5-31, 4771 kb/s, 90k tbn, 29.97 tbc[/B]
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
```

---

