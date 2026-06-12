---
title: "Error in playing a video in mplayer and vlc"
date: 2017-01-10
forum: Multimedia Software
---

### Post by dilantha on 2017-01-10
Hi,
Im trying to play a video using mplayer and vlc but getting below errors in both apps.

Mplayer 
```
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code
[mpeg4 @ 0x7f6532d27a20]marker does not match f_code



```

VLC

```
[aac @ 0x7fbf00c027c0] More than one AAC RDB per ADTS frame is not implemented. Update your Libav version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
[aac @ 0x7fbf00c027c0] Error decoding AAC frame header.
[aac @ 0x7fbf00c027c0] Reserved bit set.
[aac @ 0x7fbf00c027c0] channel element 2.7 is not allocated
[aac @ 0x7fbf00c027c0] channel element 3.0 is not allocated
[aac @ 0x7fbf00c027c0] More than one AAC RDB per ADTS frame is not implemented. Update your Libav version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
[aac @ 0x7fbf00c027c0] Error decoding AAC frame header.
[aac @ 0x7fbf00c027c0] Reserved bit set.
[aac @ 0x7fbf00c027c0] channel element 2.7 is not allocated
[aac @ 0x7fbf00c027c0] channel element 3.0 is not allocated



```

Output for > ffmpeg -i Movie.avi is

```

ffmpeg version 3.2.2 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.3)
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --mandir=/usr/share/man --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libfreetype --enable-gnutls --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvidstab --enable-libwavpack --enable-nvenc
  libavutil      55. 34.100 / 55. 34.100
  libavcodec     57. 64.101 / 57. 64.101
  libavformat    57. 56.100 / 57. 56.100
  libavdevice    57.  1.100 / 57.  1.100
  libavfilter     6. 65.100 /  6. 65.100
  libavresample   3.  1.  0 /  3.  1.  0
  libswscale      4.  2.100 /  4.  2.100
  libswresample   2.  3.100 /  2.  3.100
  libpostproc    54.  1.100 / 54.  1.100
[avi @ 0x37e5d00] Something went wrong during header parsing, tag [170]Qw[33] has size 1908644170, I will ignore it and try to continue anyway.
[mpeg4 @ 0x37e7100] time_increment_bits 0 is invalid in relation to the current bitstream, this is likely caused by a missing VOL header
[mpeg4 @ 0x37e7100] time_increment_bits set to 4 bits, based on bitstream analysis
[mpeg4 @ 0x37e7100] looks like this file was encoded with (divx4/(old)xvid/opendivx) -> forcing low_delay flag
[mpeg4 @ 0x37e7100] warning: first frame is no keyframe
[mpeg4 @ 0x37e7100] I cbpy damaged at 0 0
[mpeg4 @ 0x37e7100] Error at MB: 0
[mpeg4 @ 0x37e7100] marker does not match f_code
    Last message repeated 32 times
[mpeg4 @ 0x37e7100] concealing 1125 DC, 1125 AC, 1125 MV errors in P frame
Input #0, avi, from 'movie.mp4':
  Metadata:
    encoder         : VirtualDubMod 1.5.10.3 | www.virtualdub-fr.org || (build 2550/release)
  Duration: 00:53:34.42, start: 0.000000, bitrate: 2087 kb/s
    Stream #0:0: Video: mpeg4 (XVID / 0x44495658), yuv420p, 720x400, 23.98 fps, 23.
```98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0:1: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 192 kb/s

I have also installed ubuntu-restricted-extras package but still no luck :(. Any help on this would be really appreciated

Thanks

---

### Post by fernandohintzej on 2017-01-10
Hey, you seem to know more about Linux than me haha but I'm gonna try to help you anyway.

When I used Windows I got this cool codec pack called CCCP. After installing that I had no issues with video codecs ever again (I watch a lot of anime and other stuff). Didn't have issues with subtitles either). When I move to Ubuntu (I'm running Ubuntu Mate 16.10 at this moment) I looked for a similar codec pack that would work just as fine as CCCP did, and I found this thread: [https://ubuntuforums.org/showthread.php?t=968437](https://ubuntuforums.org/showthread.php?t=968437) . I read the comments and found one that said "*In short, install Gstreamer codecs and w32codecs, and then install SMPlayer, and you should be good to go!*", and thats what I did.

Installing the Gstreamer codecs was easy (I think you just need to add a repository and run "apt-get install gstreamer" to get it done), but the w32codecs were more of a challenge (at least for a not-to-advanced user like me haha). While I was looking how to get the w32codecs I read somewhere that they were ment to play really old digital videos, so you could never even use them, but I got them installed anyway just in case. I'm leaving the link here if you want to get them ([http://www.deb-multimedia.org/dists/unstable/non-free/binary-i386/package/w32codecs](http://www.deb-multimedia.org/dists/unstable/non-free/binary-i386/package/w32codecs)) (thats the package, getting them installed is another issue, but I'm sure you can figure it out).

Hope it helps you!

---

### Post by mc4man on 2017-01-10
Try,
```
ffmpeg -i Movie.avi -c copy whatever.avi
```
See if whatever.avi plays any better.

---

### Post by Yellow Pasque on 2017-01-10
```
encoder         : VirtualDubMod 1.5.10.3 | www.virtualdub-fr.org || (build 2550/release)
```

If you google the "marker does not match f_code" message, you will see similar complaints about videos encoded with VirtualDubMod. I guess it is/was not the best encoder in the world. Hopefully, mc4man's command will clean up the video.

---

### Post by dilantha on 2017-01-11
Hi Thanks a lot for the reply. When i ran the command i got 

[avi @ 0x2cc89c0] Non-monotonous DTS in output stream 0:1; previous: 3713, current: 1038; changing to 3714. This may result in incorrect timestamps in the output file.

Still the converted video file did not play.However now i get a different error in mplayer

Too many audio packets in the buffer: (4096 in 2050048 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  12.7 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 62 0 
[ac3 @ 0x7fbff0f17a20]frame sync error
[ac3 @ 0x7fbff0f17a20]frame CRC mismatch
[ac3 @ 0x7fbff0f17a20]frame sync error
[ac3 @ 0x7fbff0f17a20]frame CRC mismatch
[ac3 @ 0x7fbff0f17a20]frame sync error
[ac3 @ 0x7fbff0f17a20]frame CRC mismatch
[ac3 @ 0x7fbff0f17a20]frame sync error
[ac3 @ 0x7fbff0f17a20]frame CRC mismatch

No errors in VLC. But the video doesnt play :(

---

### Post by Yellow Pasque on 2017-01-11
I see suggestions to try DivFix++ as a possible solution if ffmpeg copy doesn't work.
You will need wxheaders-3.0 package

[https://sourceforge.net/projects/divfixpp/files/DivFix%2B%2B/v0.34/DivFix%2B%2B_v0.34-src.tar.bz2/download](https://sourceforge.net/projects/divfixpp/files/DivFix%2B%2B/v0.34/DivFix%2B%2B_v0.34-src.tar.bz2/download)

```
tar xjf DivFix++_v0.34-src.tar.bz2
cd DivFix++_v0.34/
make
./DivFix++
```

---

