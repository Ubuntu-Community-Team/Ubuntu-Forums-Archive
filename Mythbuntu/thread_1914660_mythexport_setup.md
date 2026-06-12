---
title: "mythexport setup"
date: 2012-01-24
forum: Mythbuntu
---

### Post by mitchell2345 on 2012-01-24
Hi,

Just got an iPad and want to setup Mythtv to export recordings that I can plan on my ipad.  I figured it would be easy to use mythexport for this.  I installed it from MCC and went to the config page.  setup my dir, userjob1 etc.  When I tell a recording to run the userjob i get this isn the mythexport log:

```
mitchell@myth:/var/log/mythtv$ cat mythexport.log 
January 24 18:05:10 myth /usr/bin/mythexport-daemon[7318]: Starting Processing:  1327449910
ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jan  4 2012 16:21:50 with gcc 4.6.1
  configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avfilter    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  swscale     configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  postproc    configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[NULL @ 0x85b7400] start time is not set in av_estimate_timings_from_pts
Input #0, mpegts, from '/tv/d2/recordings/2241_20120124170000.mpg':
  Duration: 00:59:54.13, start: 21598.141889, bitrate: 14500 kb/s
  Program 1 
    Stream #0.0[0xf51]: Video: mpeg2video (Main), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 38810 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0xf52](eng): Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.2[0xf53]: Data: [134][0][0][0] / 0x0086
File for preset 'slowfirstpass' not found
January 24 18:10:11 myth /usr/bin/mythexport-daemon[7318]: ERROR: No resulting file from ffmpeg, most likely your ffmpeg failed.  Enable debugging and test by hand. at line 453 in /usr/bin/mythexport-daemon
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: ERROR: Directory  is not writeable.
 at line 283 in /usr/bin/mythexport-daemon
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: Creating mysql dump
sh: cannot create /mythimport.sql: Permission denied
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: ERROR: mysqldump -hlocalhost -umythtv -pmythtv -P3306 mythconverg recorded recordedseek recordedrating recordedprogram recordedmarkup recordedcredits --where="(chanid='6041' and starttime='2012-01-21 22:30:00')" --no-create-db --no-create-info > /mythimport.sql 2>&1 failed. at line 297 in /usr/bin/mythexport-daemon
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: Copying /tv/d2/recordings/6041_20120121223000.mpg to /6041_20120121223000.mpg
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: Unable to copy /tv/d2/recordings/6041_20120121223000.mpg to /6041_20120121223000.mpg at line 319 in /usr/bin/mythexport-daemon
January 24 18:42:37 myth /usr/bin/mythexport-daemon[7318]: Caught SIGTERM:  exiting gracefully
January 24 18:42:37 myth /usr/bin/mythexport-daemon[7318]: Stopping Processing:  1327452157
January 24 18:42:41 myth /usr/bin/mythexport-daemon[8466]: Starting Processing:  1327452161
January 24 18:43:45 myth /usr/bin/mythexport-daemon[8466]: Caught SIGTERM:  exiting gracefully
January 24 18:43:45 myth /usr/bin/mythexport-daemon[8466]: Stopping Processing:  1327452225
January 24 18:43:48 myth /usr/bin/mythexport-daemon[8493]: Starting Processing:  1327452228
January 24 18:43:48 myth /usr/bin/mythexport-daemon[8493]: query = select id, type, param from mythexport_job_queue order by id at line 489 in /usr/bin/mythexport-daemon
```

can someone give me some pointers?  Looks like im getting some perm issues.

Thanks,
Mitchell

---

### Post by nickrout on 2012-01-24
> **mitchell2345 said:**
> Hi,

Just got an iPad and want to setup Mythtv to export recordings that I can plan on my ipad.  I figured it would be easy to use mythexport for this.  I installed it from MCC and went to the config page.  setup my dir, userjob1 etc.  When I tell a recording to run the userjob i get this isn the mythexport log:

```
mitchell@myth:/var/log/mythtv$ cat mythexport.log 
January 24 18:05:10 myth /usr/bin/mythexport-daemon[7318]: Starting Processing:  1327449910
ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jan  4 2012 16:21:50 with gcc 4.6.1
  configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avfilter    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  swscale     configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  postproc    configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[NULL @ 0x85b7400] start time is not set in av_estimate_timings_from_pts
Input #0, mpegts, from '/tv/d2/recordings/2241_20120124170000.mpg':
  Duration: 00:59:54.13, start: 21598.141889, bitrate: 14500 kb/s
  Program 1 
    Stream #0.0[0xf51]: Video: mpeg2video (Main), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 38810 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0xf52](eng): Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.2[0xf53]: Data: [134][0][0][0] / 0x0086
File for preset 'slowfirstpass' not found
January 24 18:10:11 myth /usr/bin/mythexport-daemon[7318]: ERROR: No resulting file from ffmpeg, most likely your ffmpeg failed.  Enable debugging and test by hand. at line 453 in /usr/bin/mythexport-daemon
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: ERROR: Directory  is not writeable.
 at line 283 in /usr/bin/mythexport-daemon
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: Creating mysql dump
sh: cannot create /mythimport.sql: Permission denied
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: ERROR: mysqldump -hlocalhost -umythtv -pmythtv -P3306 mythconverg recorded recordedseek recordedrating recordedprogram recordedmarkup recordedcredits --where="(chanid='6041' and starttime='2012-01-21 22:30:00')" --no-create-db --no-create-info > /mythimport.sql 2>&1 failed. at line 297 in /usr/bin/mythexport-daemon
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: Copying /tv/d2/recordings/6041_20120121223000.mpg to /6041_20120121223000.mpg
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: Unable to copy /tv/d2/recordings/6041_20120121223000.mpg to /6041_20120121223000.mpg at line 319 in /usr/bin/mythexport-daemon
January 24 18:42:37 myth /usr/bin/mythexport-daemon[7318]: Caught SIGTERM:  exiting gracefully
January 24 18:42:37 myth /usr/bin/mythexport-daemon[7318]: Stopping Processing:  1327452157
January 24 18:42:41 myth /usr/bin/mythexport-daemon[8466]: Starting Processing:  1327452161
January 24 18:43:45 myth /usr/bin/mythexport-daemon[8466]: Caught SIGTERM:  exiting gracefully
January 24 18:43:45 myth /usr/bin/mythexport-daemon[8466]: Stopping Processing:  1327452225
January 24 18:43:48 myth /usr/bin/mythexport-daemon[8493]: Starting Processing:  1327452228
January 24 18:43:48 myth /usr/bin/mythexport-daemon[8493]: query = select id, type, param from mythexport_job_queue order by id at line 489 in /usr/bin/mythexport-daemon
```

can someone give me some pointers?  Looks like im getting some perm issues.

Thanks,
Mitchell

Have you set the output directory to / ?

Set it somewhere sensible :)

---

### Post by mitchell2345 on 2012-01-24
yes i did.  in the setup page.:

```
mitchell@myth:~$ cat /etc/mythtv/mythexport/mythexport.cfg
dir=/tv/d1/Exports
mitchell@myth:~$ ls /tv/d1
backup   coverart    Exports  livetv     recordings  screenshots  trailers
banners  db_backups  fanart   lost+found  picturesmitchell@myth:~$ 

```

---

### Post by nickrout on 2012-01-25
> **mitchell2345 said:**
> yes i did.  in the setup page.:

```
mitchell@myth:~$ cat /etc/mythtv/mythexport/mythexport.cfg
dir=/tv/d1/Exports
mitchell@myth:~$ ls /tv/d1
backup   coverart    Exports  livetv     recordings  screenshots  trailers
banners  db_backups  fanart   lost+found  picturesmitchell@myth:~$ 

```

well this line```
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: Unable to copy /tv/d2/recordings/6041_20120121223000.mpg to /6041_20120121223000.mpg at line 319 in /usr/bin/mythexport-daemon

```

seems to indicate that it is trying to copy the file to / at line 319 of /usr/bin/mythexport-daemon

So look there, something is wrong if it is trying to copy to /

---

### Post by SpaceBas on 2012-04-22
> **nickrout said:**
> well this line```
January 24 18:28:11 myth /usr/bin/mythexport-daemon[7318]: Unable to copy /tv/d2/recordings/6041_20120121223000.mpg to /6041_20120121223000.mpg at line 319 in /usr/bin/mythexport-daemon

```

seems to indicate that it is trying to copy the file to / at line 319 of /usr/bin/mythexport-daemon

So look there, something is wrong if it is trying to copy to /

For those curious, or finding this thread via search, the error is actually a few lines above the permissions errors. The ffmpeg flags used in MythExport's .pm files is no longer valid syntax, and so the conversion never happens and thus there's no file to copy at the end of the job. 

here's some insight and potential solutions:

[http://ubuntuforums.org/showthread.php?t=1926009](http://ubuntuforums.org/showthread.php?t=1926009)

---

