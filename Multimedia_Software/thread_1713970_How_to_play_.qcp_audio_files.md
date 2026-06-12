---
title: "How to play .qcp audio files"
date: 2011-03-24
forum: Multimedia Software
---

### Post by pivotraze on 2011-03-24
Is it at all fathomable to play .qcp files on Ubuntu 11.04? I REALLY want to... I recorded this totally amazing trumpet player, and I need to play this audio to learn more.

"There is no application installed for RIFF audio files." Is what I get when I double click it.

WAIT! VLC does it! OMG YAY! With skips in the audio :( How can I convert to mp3

Help? :)

HERE! Download this: [http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

It converts any mobile file to a file of your choice, it worked PERFECTLY for my .qcp file, converted it from qcp to mp3 with no problem, no skips, full file.

---

### Post by Manolicious on 2011-08-31
didn't work for me

```

>> Command executed:
"/opt/MIKSOFT/MobileMediaConverter/lib/ffmpeg" -y -vn -i "/home/user/file.qcp" -acodec libmp3lame -ac 2 -ar 44100 -ab 192k -f mp3 -map_meta_data "/home/user/file.mp3":"/home/user/file.qcp" "/home/user/file.mp3"

>> Result: 
FFmpeg version 0.6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  1 2010 22:37:53 with gcc 4.4.3
  configuration: --enable-libfaac --enable-libmp3lame --enable-libvpx --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-gpl --enable-nonfree --enable-version3 --enable-libvorbis
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.11. 0 /  0.11. 0
[qcp @ 0x9b61420]Unknown codec GUID.
/home/user/file.qcp: Invalid data found when processing input
----------------------------



```

---

### Post by andrew.46 on 2011-09-01
Current FFmpeg has a decoder for these files:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]ffmpeg -codecs | grep -i qcelp[/COLOR]**
ffmpeg version N-32221-g76ba894, Copyright (c) 2000-2011 the FFmpeg developers
  built on Aug 31 2011 08:50:04 with gcc 4.5.2
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-zlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libxvid --enable-libfreetype --enable-x11grab --enable-nonfree --enable-gpl --enable-version3
  libavutil    51. 14. 0 / 51. 14. 0
  libavcodec   53. 12. 0 / 53. 12. 0
  libavformat  53. 10. 0 / 53. 10. 0
  libavdevice  53.  3. 0 / 53.  3. 0
  libavfilter   2. 37. 0 /  2. 37. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
**[COLOR="Red"] D A    qcelp           QCELP / PureVoice[/COLOR]**

```

Oddly enough my copy of MPlayer seg faults with these files. Sample here:

```

wget 'http://samples.mplayerhq.hu/A-codecs/qcp/When_I_Need_You_Celine_Dion.qcp'

```

---

### Post by dniMretsaM on 2011-09-01
You could try converting it with VLC.

---

