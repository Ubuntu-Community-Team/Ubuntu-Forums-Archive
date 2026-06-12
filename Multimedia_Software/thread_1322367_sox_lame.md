---
title: "sox lame"
date: 2009-11-10
forum: Multimedia Software
---

### Post by paxmark1 on 2009-11-10
previous problem.  sox will not convert .wma or flac to mp3 in Debian type distros (I hear tell it does it in RH land)

9.10 AMD64

I remembered that sox as is does not like lame  (I just updated ffmpeg to the SVN sucessfully)

In terminal

sox --help-format mp3    yields

Cannot find a format called `mp3'     

I got the 14.3 tarball.  configures well and lame is configured correctly

It borked on the make -s

So I shifted over to ~/SVN    and pulled down the cvs

Again, it configured well

make -s still borks

paxmark@raunes:~/SVN/sox$ make -s
Making all in lpc10
Making all in libgsm
Making all in src
util.c:24: warning: no previous prototype for &#8216;lsx_strcasecmp&#8217;
util.c:37: warning: no previous prototype for &#8216;lsx_strncasecmp&#8217;
sox-fmt.c: In function &#8216;write_header&#8217;:
sox-fmt.c:81: warning: dereferencing type-punned pointer will break strict-aliasing rules
ffmpeg.c: In function &#8216;audio_decode_frame&#8217;:
ffmpeg.c:130: warning: &#8216;avcodec_decode_audio2&#8217; is deprecated (declared at /usr/local/include/libavcodec/avcodec.h:3230)
ffmpeg.c: In function &#8216;startwrite&#8217;:
ffmpeg.c:347: warning: &#8216;av_alloc_format_context&#8217; is deprecated (declared at /usr/local/include/libavformat/avformat.h:807)
In file included from mp3.c:212:
mp3-util.h: In function &#8216;write_comments&#8217;:
mp3-util.h:45: warning: passing argument 2 of &#8216;p->id3tag_set_pad&#8217; with different width due to prototype
mp3.c: In function &#8216;get_id3v2_tag_size&#8217;:
mp3.c:554: warning: passing argument 2 of &#8216;fseeko&#8217; with different width due to prototype
mp3.c:560: warning: passing argument 2 of &#8216;fread&#8217; with different width due to prototype
mp3.c:567: warning: passing argument 3 of &#8216;strncmp&#8217; with different width due to prototype
mp3.c:548: warning: unused variable &#8216;p&#8217;
mp3.c: In function &#8216;rewrite_id3v2_tag&#8217;:
mp3.c:587: warning: passing argument 2 of &#8216;lsx_realloc&#8217; with different width due to prototype
mp3.c:598: warning: passing argument 2 of &#8216;p->id3tag_set_pad&#8217; with different width due to prototype
mp3.c:599: warning: passing argument 3 of &#8216;p->lame_get_id3v2_tag&#8217; with different width due to prototype
mp3.c:602: warning: passing argument 2 of &#8216;p->id3tag_set_pad&#8217; with different width due to prototype
mp3.c:603: warning: passing argument 3 of &#8216;p->lame_get_id3v2_tag&#8217; with different width due to prototype
mp3.c:609: warning: passing argument 2 of &#8216;fseeko&#8217; with different width due to prototype
mp3.c:611: warning: passing argument 2 of &#8216;fwrite&#8217; with different width due to prototype
mp3.c:611: warning: passing argument 3 of &#8216;fwrite&#8217; with different width due to prototype
mp3.c: In function &#8216;rewrite_tags&#8217;:
mp3.c:627: warning: passing argument 2 of &#8216;fseeko&#8217; with different width due to prototype
mp3.c:651: warning: passing argument 2 of &#8216;fseeko&#8217; with different width due to prototype
mp3.c:666: warning: passing argument 2 of &#8216;fwrite&#8217; with different width due to prototype
mp3.c:666: warning: passing argument 3 of &#8216;fwrite&#8217; with different width due to prototype
sndfile.c: In function &#8216;sf_stop_stub&#8217;:
sndfile.c:224: warning: unused parameter &#8216;sndfile&#8217;
/usr/bin/ld: /usr/local/lib/libavformat.a(allformats.o): relocation R_X86_64_32 against `aac_demuxer' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavformat.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libsox.la] Error 1
make: *** [all-recursive] Error 1

previously I also used prior autoreconf -i from the debian readme  subsection of the source directory.  same error codes

I have always done make distclean after each failed make

Any ideas on how to comile either sox-14.3 or the cvs on 9.10  

tia  peace

---

### Post by HappyFeet on 2009-11-10
Have you tried **soundconverter** for what you are trying to do?

---

### Post by paxmark1 on 2009-11-11
no but it looks like it would work.   Home page shows it has some faithful developers.  dependencies not too crazy.

I will wait to mark it solved to see if someone else has compilation tips for sox. I do like the command line, but am not a zealot.

---

### Post by mc4man on 2009-11-11
don't see any issue building using a straight ./configure,  make.
> .................
/bin/bash ../libtool --silent --tag=CC  --silent --mode=link gcc -Wtraditional-conversion  -g -O2 -D_FORTIFY_SOURCE=2 -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -fopenmp -avoid-version -module -Wl,-z,defs -o example3 example3.o libsox.la -lasound -lamrnb  -lao  -lavformat -lavcodec -lavutil   -lFLAC  -lvorbisenc -lvorbisfile -lvorbis  -logg -lgsm  -lmad -lid3tag -lz -lmp3lame  -lpulse -lpulse-simple   -lvorbisenc -lvorbisfile -lvorbis  -logg -lwavpack -lsndfile   -lm 
make  all-am
make[2]: Entering directory `/home/doug/Download/sox-14.3.0/src'
make[2]: Leaving directory `/home/doug/Download/sox-14.3.0/src'
make[1]: Leaving directory `/home/doug/Download/sox-14.3.0/src'
make[1]: Entering directory `/home/doug/Download/sox-14.3.0'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/doug/Download/sox-14.3.0'



Your erroring  out on your ffmpeg, though I didn't see any of the mp3 warnings either ( atm using ffmpeg -r 19777, shared and static

soundkonverter should do just fine, ( no wmal, should handle wma3, probably has better control over mp3 anyway

---

### Post by paxmark1 on 2009-11-12
thanks,  I will amend to fixed.

---

