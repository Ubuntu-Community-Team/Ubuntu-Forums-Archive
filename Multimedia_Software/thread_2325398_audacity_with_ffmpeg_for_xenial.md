---
title: "audacity with ffmpeg for xenial"
date: 2016-05-22
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2016-05-22
I am wondering if there is a ppa for Ubuntu 16.04 with an up to date version of audacity with ffmpeg support. I tried to compile it myself but didn't work.
```

FFmpeg.h: In function ‘AVOutputFormat* av_oformat_next(AVOutputFormat*)’:
FFmpeg.h:692:25: error: conflicting declaration of C function ‘AVOutputFormat* av_oformat_next(AVOutputFormat*)’
       (AVOutputFormat *f),
                         ^
FFmpeg.h:486:18: note: in definition of macro ‘FFMPEG_FUNCTION_WITH_RETURN’
       inline r n a                                                      \
                  ^
In file included from FFmpeg.h:44:0,
                 from AudacityApp.cpp:73:
/usr/include/x86_64-linux-gnu/libavformat/avformat.h:1928:17: note: previous declaration ‘AVOutputFormat* av_oformat_next(const AVOutputFormat*)’
 AVOutputFormat *av_oformat_next(const AVOutputFormat *f);
                 ^
In file included from AudacityApp.cpp:73:0:
FFmpeg.h: In function ‘int av_fifo_size(AVFifoBuffer*)’:
FFmpeg.h:759:23: error: conflicting declaration of C function ‘int av_fifo_size(AVFifoBuffer*)’
       (AVFifoBuffer *f),
                       ^
FFmpeg.h:486:18: note: in definition of macro ‘FFMPEG_FUNCTION_WITH_RETURN’
       inline r n a                                                      \
                  ^
In file included from FFmpeg.h:45:0,
                 from AudacityApp.cpp:73:
/usr/include/x86_64-linux-gnu/libavutil/fifo.h:76:5: note: previous declaration ‘int av_fifo_size(const AVFifoBuffer*)’
 int av_fifo_size(const AVFifoBuffer *f);
     ^
In file included from AudacityApp.cpp:73:0:
FFmpeg.h: In function ‘AVDictionaryEntry* av_dict_get(AVDictionary*, const char*, const AVDictionaryEntry*, int)’:
FFmpeg.h:805:82: error: conflicting declaration of C function ‘AVDictionaryEntry* av_dict_get(AVDictionary*, const char*, const AVDictionaryEntry*, int)’
       (AVDictionary *m, const char *key, const AVDictionaryEntry *prev, int flags),
                                                                                  ^
FFmpeg.h:486:18: note: in definition of macro ‘FFMPEG_FUNCTION_WITH_RETURN’
       inline r n a                                                      \
                  ^
In file included from /usr/include/x86_64-linux-gnu/libavcodec/avcodec.h:37:0,
                 from FFmpeg.h:43,
                 from AudacityApp.cpp:73:
/usr/include/x86_64-linux-gnu/libavutil/dict.h:104:20: note: previous declaration ‘AVDictionaryEntry* av_dict_get(const AVDictionary*, const char*, const AVDictionaryEntry*, int)’
 AVDictionaryEntry *av_dict_get(const AVDictionary *m, const char *key,
                    ^

```

```
ffmpeg version 2.8.6-1ubuntu2.1~ppa2

```

Audacity 2.1.2

Thanks.

---

### Post by mc4man on 2016-05-22
daily ppa? - [https://launchpad.net/~audacity-team/+archive/ubuntu/daily](https://launchpad.net/~audacity-team/+archive/ubuntu/daily)

---

### Post by monkeybrain20122 on 2016-05-22
> **mc4man said:**
> daily ppa? - [https://launchpad.net/~audacity-team/+archive/ubuntu/daily](https://launchpad.net/~audacity-team/+archive/ubuntu/daily)

Hi, Thanks. It turns out that the version in the repo already has ffmpeg enabled. Somehow I thought it was a "free" version without ffmpeg.

---

### Post by mc4man on 2016-05-22
> **monkeybrain20122 said:**
> Hi, Thanks. It turns out that the version in the repo already has ffmpeg enabled. Somehow I thought it was a "free" version without ffmpeg.
Ok - I assumed you knew that...
Anyway your compile error, if it comes up again, likely can be fixed with --disable-dynamic-loading configure option (when in doubt sometimes checking the debian/rules file of a successful package build is useful, ex. - 
```
configure_flags := \
	--disable-dynamic-loading \
	--with-expat=system \
	--with-ffmpeg=system \
	--with-lame=system \
	--with-libflac=system \
	--with-libid3tag=system \
	--with-libmad=system \
	--with-libsndfile=system \
	--with-libsoxr=system \
	--with-libtwolame=system \
	--with-libvamp=system \
	--with-libvorbis=system \
	--with-lv2=system \
	--with-midi=system \
	--with-portaudio=system \
	--with-portsmf=system \
	--with-sbsms=system \
	--with-soundtouch=system \
	$(NULL)
```

---

