---
title: "Transcode 1.0.6 build problem"
date: 2009-01-10
forum: Multimedia Software
---

### Post by WildeBeest on 2009-01-10
When I run the make command I get the following errors
I use the basic ./configure command first


```

import_ffmpeg.c: In function 'import_ffmpeg_open':
import_ffmpeg.c:364: error: 'AVCodecContext' has no member named 'error_resilience'


make[3]: *** [import_ffmpeg.lo] Error 1
make[3]: Leaving directory `/home/willy/Code/transcode-1.0.6/import'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/willy/Code/transcode-1.0.6/import'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/willy/Code/transcode-1.0.6'
make: *** [all] Error 2

```

As far as I can tell, the structure "AVCodecContext" is defined in "/usr/include/ffmpeg/avcodec.h".
It has "error_resilience" as one of the member variables.

I believe this is the only file that "AVCodecContext" is defined in. From what I can tell by looking at the code, there is no compiler DEF that would exclude the member variable.

Why does the compiler not see this member variable?

I have written my share of c & c++ applications for many other OS's, but I'm relatively new to linux.

if anyone can shed some light on this, it would be appreciated.

---

### Post by wolfen69 on 2009-01-10
what exactly are you trying to "make"?

---

### Post by WildeBeest on 2009-01-10
transcode 1.0.6

[http://www.transcoding.org/cgi-bin/transcode?General_Information]("http://www.transcoding.org/cgi-bin/transcode?General_Information")

[http://www.transcoding.org/cgi-bin/transcode?Download]("http://www.transcoding.org/cgi-bin/transcode?Download")

Of all you experts on here, someone most know what's going on... :(

---

### Post by WildeBeest on 2009-01-12
ttt

---

### Post by tvijlbrief on 2009-01-24
> **WildeBeest said:**
> When I run the make command I get the following errors


Why does the compiler not see this member variable?

I have written my share of c & c++ applications for many other OS's, but I'm relatively new to linux.

if anyone can shed some light on this, it would be appreciated.

Well, you are probably including from an avcodec.h other than the one in /usr/include. Eg from /usr/local/include/libavcodec/avcodec.h if you've just build your own ffmpeg. You should uninstall the ffmpeg from ubuntu to avoid these and other confusions.

Newer ffmpeg versions don't have that member. I tried downloading the transcode 1.1 version but the download server is down at the moment. The 1.0.6 version exhibits the same problem for me. I edited the code by hand at some places, but it is probably wiser to get a newer transcode version...

Edit: Just downloaded transcode 1.1.0 and it compiles just fine with the latest ffmpeg

---

