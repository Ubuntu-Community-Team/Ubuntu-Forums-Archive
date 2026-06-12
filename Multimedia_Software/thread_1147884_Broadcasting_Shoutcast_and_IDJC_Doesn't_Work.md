---
title: "Broadcasting Shoutcast and IDJC Doesn't Work"
date: 2009-05-03
forum: Multimedia Software
---

### Post by mgoblue on 2009-05-03
Installing normally, I didn't have the option to broadcast to shoutcast, only icecast. It is saying MP3 streaming is not available :(

I tried this threads solution: [http://ubuntuforums.org/showpost.php?p=5200135&postcount=5](http://ubuntuforums.org/showpost.php?p=5200135&postcount=5)

but make doesn't go through all the way

```

/usr/local/lib/libavformat.a(riff.o): In function `ff_parse_specific_params':
/home/kevin/x264/ffmpeg/libavformat/riff.c:477: undefined reference to `av_gcd'
/usr/local/lib/libavformat.a(riff.o): In function `put_wav_header':
/home/kevin/x264/ffmpeg/libavformat/riff.c:299: undefined reference to `av_log'
/usr/local/lib/libavformat.a(riff.o): In function `get_wav_header':
/home/kevin/x264/ffmpeg/libavformat/riff.c:428: undefined reference to `av_mallocz'
/usr/local/lib/libavformat.a(rtp_aac.o): In function `ff_rtp_send_aac':
/home/kevin/x264/ffmpeg/libavformat/rtp_aac.c:70: undefined reference to `av_log'
/home/kevin/x264/ffmpeg/libavformat/rtp_aac.c:71: undefined reference to `av_log'
collect2: ld returned 1 exit status
make[2]: *** [idjcmixer] Error 1
make[2]: Leaving directory `/home/kevin/Desktop/idjc-0.7.14/c'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kevin/Desktop/idjc-0.7.14'
make: *** [all] Error 2

```

Is the last few lines.  Any help?  Or other suggestions on how to broadcast to a shoutcast server?

---

### Post by mgoblue on 2009-05-06
Bump

---

### Post by StephenF on 2009-05-06
Add --disable-ffmpeg to the configure options. This will get it compiled but the resultant build won't be able to play m4a files.

---

