---
title: "Unknown encoder 'libxvid' - ffmpeg error"
date: 2012-04-11
forum: Multimedia Software
---

### Post by Gibsonbc on 2012-04-11
I am trying to convert .mts videos from my Sony NEX5N camera to .avi files using ffmpeg.  I compiled ffmpeg by following FakeOutdoorsman's guide ([http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)) and installed the extras from the medibuntu repository here ([http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283))  - also thanks to FOM!  Then I installed WinFF for a simple GUI beginner friendly way to get going.  However, I've been at this a while and I keep getting the error message when I hit convert .....

"ffmpeg version git-2012-04-12-277f20c Copyright (c) 2000-2012 the FFmpeg developers
  built on Apr 11 2012 17:57:57 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab
  libavutil      51. 46.100 / 51. 46.100
  libavcodec     54. 14.101 / 54. 14.101
  libavformat    54.  3.100 / 54.  3.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 67.101 /  2. 67.101
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 11.100 /  0. 11.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, mpegts, from '/home/gibsonbc/Videos/Brian Camera/00000.MTS':
  Duration: 00:00:46.04, start: 1.000033, bitrate: 16463 kb/s
  Program 1 
    Stream #0:0[0x1011]: Video: h264 (High) (HDMV / 0x564D4448), yuv420p, 1920x1080 [SAR 1:1 DAR 16:9], 59.96 fps, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0:1[0x1100]: Audio: ac3 (AC-3 / 0x332D4341), 48000 Hz, stereo, s16, 256 kb/s
    Stream #0:2[0x1200]: Subtitle: hdmv_pgs_subtitle ([144][0][0][0] / 0x0090)
[COLOR=Blue]Please use -b:a or -b:v, -b is ambiguous[/COLOR]
[COLOR=Red]Unknown encoder 'libxvid'[/COLOR]
Press Enter to Continue"

Before I could get anything from the medibuntu repos via terminal I had to run the following code because I kept getting the error message that some things failed to download .... "no pubkey"

Quote: 	 	 		 			 				sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

Now I only get that error message for virtualbox when running sudo apt-get update.

I've read other threads where people are encountering similar issues but nothing I've tried as worked completely.  Usually just opens the door to other problems.  I'm sure this is probably something I've screwed up by trying lots of solutions....:confused:

---

### Post by FakeOutdoorsman on 2012-04-12
> **Gibsonbc said:**
> ```
Unknown encoder 'libxvid'
```

You get this message because ffmpeg has not been compiled with *--enable-libxvid*. The compile guide used to include this, but I thought it was superfluous and removed it because ffmpeg includes a native encoder that is probably as good or better. I didn't think about WinFF when I decided to remove it.

You have several options:
A. Change the WinFF preset to use *-vcodec mpeg4* instead of *-vcodec libxvid*.

B. Remove your compiled ffmpeg and use the version from the repository (or via Medibuntu if you like). This should work with WinFF.

C. Use ffmpeg directly. The following commands do the same thing, but use different syntax depending on your ffmpeg version. I don't keep up with the repository "ffmpeg" syntax anymore, so I'm not sure what works for it (if you decide to use repo ffmpeg and use ffmpeg directly). If one command doesn't work then try the other. I don't know what WinFF preset you tried, but this might achieve something similar. Lower qscale and aq values create a higher quality output.

Older syntax (repository ffmpeg might still use this):
```
ffmpeg -i input -vcodec mpeg4 -qscale 3 -acodec libmp3lame -aq 4 output.mkv
```
Recent syntax (recently compiled FFmpeg):
```
ffmpeg -i input -c:v mpeg4 -q:v 4 -c:a libmp3lame -q:a 4 output.mkv
```

---

