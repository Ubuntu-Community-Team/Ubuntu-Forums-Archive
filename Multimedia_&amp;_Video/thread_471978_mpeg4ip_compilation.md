---
title: "mpeg4ip compilation"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by bioborg on 2007-06-12
I am running Feisty on AMD64.  I downloaded mpeg4ip 1.5.01 and ./bootstrap worked fine.  I had all the dependencies installed.  When I typed make, it failed.  I googled the failing instruction, and found a reference on the freebsd list to the same error.  I applied the patches, and then get a new error.  Here's the first error and the patches:
On 5/2/07, Nick Markovich <nickmarko at gmail.com> wrote:
> -- Original message by *Bruce M Simpson --*
> this is with ffmpeg-devel-2007.03.31_1 installed automatically by
> portupgrade.
>
> The following two patches seem to be needed.
>
> In file included from ffmpeg.h:30,
>                  from ffmpeg.cpp:26:
> /usr/local/include/ffmpeg/avcodec.h:2450: warning: `ImgReSampleContext'
> is deprecated (declared at /usr/local/include/ffmpeg/avcodec.h:2447)
> /usr/local/include/ffmpeg/avcodec.h:2457: warning: `ImgReSampleContext'
> is deprecated (declared at /usr/local/include/ffmpeg/avcodec.h:2447)
> /usr/local/include/ffmpeg/avcodec.h:2461: warning: `ImgReSampleContext'
> is deprecated (declared at /usr/local/include/ffmpeg/avcodec.h:2447)
> /usr/local/include/ffmpeg/avcodec.h:2463: warning: `ImgReSampleContext'
> is deprecated (declared at /usr/local/include/ffmpeg/avcodec.h:2447)
> ffmpeg.cpp: In function `codec_data_t* ffmpeg_create(const char*, const
> char*, int, int, format_list_t*, audio_info_t*, const uint8_t*,
> uint32_t, audio_vft_t*, void*)':
> ffmpeg.cpp:169: error: invalid conversion from `void*' to `uint8_t*'
> ffmpeg.cpp: In function `int ffmpeg_decode(codec_data_t*,
> frame_timestamp_t*, int, int*, uint8_t*, uint32_t, void*)':
> ffmpeg.cpp:217: warning: `avcodec_decode_audio' is deprecated (declared
> at /usr/local/include/ffmpeg/avcodec.h:2743)
> ffmpeg.cpp:218: warning: `avcodec_decode_audio' is deprecated (declared
> at /usr/local/include/ffmpeg/avcodec.h:2743)
> gmake[5]: *** [ffmpeg.lo] Error 1
> gmake[5]: Leaving directory
> `/usr/ports/multimedia/mpeg4ip/work/mpeg4ip-1.5.0.1/player/plugin/audio/ffmpeg'
> gmake[4]: *** [all-recursive] Error 1
> gmake[4]: Leaving directory
> `/usr/ports/multimedia/mpeg4ip/work/mpeg4ip-1.5.0.1/player/plugin/audio'
> gmake[3]: *** [all-recursive] Error 1
> gmake[3]: Leaving directory
> `/usr/ports/multimedia/mpeg4ip/work/mpeg4ip-1.5.0.1/player/plugin'
> gmake[2]: *** [all-recursive] Error 1
> gmake[2]: Leaving directory
> `/usr/ports/multimedia/mpeg4ip/work/mpeg4ip-1.5.0.1/player'
> gmake[1]: *** [all-recursive] Error 1
> gmake[1]: Leaving directory
> `/usr/ports/multimedia/mpeg4ip/work/mpeg4ip-1.5.0.1'
> gmake: *** [all] Error 2
> *** Error code 2
>
> Stop in /usr/ports/multimedia/mpeg4ip.
> *** Error code 1
>
> Stop in /usr/ports/multimedia/mpeg4ip.
> empiric#


This was fixed on April 11th by mezz


> -------------- next part --------------
> --- mpeg4ip-1.5.0.1/player/plugin/audio/ffmpeg/ffmpeg.cpp.orig  Sun Apr
>  8 16:21:30 2007
> +++ mpeg4ip-1.5.0.1/player/plugin/audio/ffmpeg/ffmpeg.cpp       Sun Apr  8
> 16:22:05 2007
> @@ -166,7 +166,7 @@
>      break;
>    }
>    if (userdata) {
> -    ffmpeg->m_c->extradata = (void *)userdata;
> +    ffmpeg->m_c->extradata = (uint8_t *)userdata;
>      ffmpeg->m_c->extradata_size = ud_size;
>    }
>    if (avcodec_open(ffmpeg->m_c, ffmpeg->m_codec) < 0) {
> -------------- next part --------------
> --- mpeg4ip-1.5.0.1/player/plugin/video/ffmpeg/ffmpeg.cpp.orig  Sun Apr
>  8 16:22:49 2007
> +++ mpeg4ip-1.5.0.1/player/plugin/video/ffmpeg/ffmpeg.cpp       Sun Apr  8
> 16:23:20 2007
> @@ -255,7 +255,7 @@
>    }
>      break;
>    case CODEC_ID_SVQ3:
> -    ffmpeg->m_c->extradata = (void *)userdata;
> +    ffmpeg->m_c->extradata = (uint8_t *)userdata;
>      ffmpeg->m_c->extradata_size = ud_size;
>      if (vinfo != NULL) {
>        ffmpeg->m_c->width = vinfo->width;
> -- End of message --
>
> Thanks for your post, Bruce. I had that same error, but after applying
> both of your patches, mpeg4ip compiles :)
> _______________________________________________
> freebsd-multimedia at freebsd.org mailing list
> [http://lists.freebsd.org/mailman/listinfo/freebsd-multimedia](http://lists.freebsd.org/mailman/listinfo/freebsd-multimedia)
> To unsubscribe, send any mail to "freebsd-multimedia-unsubscribe at freebsd.org"
>

So now I got x264 issues.  I have the latest x264 from subversion installed with checkinstall (20070612) rev 659
I also tried with the stock x264 that comes with feisty.  Both times I get this error:

make[4]: Entering directory `/home/spoon/Desktop/mpeg4ip-1.5.0.1/server/mp4live'
if /bin/bash ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I../../include -I../../lib/mp4v2 -I../../lib/mp4av -I../../lib/msg_queue -I../../lib/rtp -I../../lib/sdp -I../../lib/utils -I../../lib -I../../lib/mpeg2ps -I../../lib/srtp -I../../player/lib -I../../player/src -I./h261    -D_REENTRANT -DNOCONTROLS -fexceptions -Wall -Wno-char-subscripts -Woverloaded-virtual -Wno-unknown-pragmas -Wno-deprecated -Wformat=2 -Wpointer-arith -Wsign-compare  -g -O2 -DMPEG4IP -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -MT video_x264.lo -MD -MP -MF ".deps/video_x264.Tpo" -c -o video_x264.lo video_x264.cpp; \
        then mv -f ".deps/video_x264.Tpo" ".deps/video_x264.Plo"; else rm -f ".deps/video_x264.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I../../include -I../../lib/mp4v2 -I../../lib/mp4av -I../../lib/msg_queue -I../../lib/rtp -I../../lib/sdp -I../../lib/utils -I../../lib -I../../lib/mpeg2ps -I../../lib/srtp -I../../player/lib -I../../player/src -I./h261 -D_REENTRANT -DNOCONTROLS -fexceptions -Wall -Wno-char-subscripts -Woverloaded-virtual -Wno-unknown-pragmas -Wno-deprecated -Wformat=2 -Wpointer-arith -Wsign-compare -g -O2 -DMPEG4IP -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -MT video_x264.lo -MD -MP -MF .deps/video_x264.Tpo -c video_x264.cpp  -fPIC -DPIC -o .libs/video_x264.o
video_x264.cpp: In member function 'virtual bool CX264VideoEncoder::Init()':
video_x264.cpp:171: error: 'struct x264_param_t::<anonymous>' has no member named 'b_cbr'
make[4]: *** [video_x264.lo] Error 1
make[4]: Leaving directory `/home/spoon/Desktop/mpeg4ip-1.5.0.1/server/mp4live'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/spoon/Desktop/mpeg4ip-1.5.0.1/server/mp4live'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/spoon/Desktop/mpeg4ip-1.5.0.1/server'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/spoon/Desktop/mpeg4ip-1.5.0.1'
make: *** [all] Error 2



Any Ideas?

---

### Post by bioborg on 2007-06-12
So, I ran ./configure --disable-x264
(I also had to roll my ffmpeg back to the ubuntu installed version...)
then ran make, and 
it died with a complaint about not being able to write a file in /usr/local/lib/mp4player_plugin -- 
I checked and that folder did not exist, so I made it, and reran make (or was I already in checkinstall?)

and it worked!.  I will attach the patches for convenience sake.

Any ideas on how to get it to work with x264

---

### Post by bioborg on 2007-06-12
Full Success!  Compiled with x264 as follows:

because this was the error while compiling x264:
video_x264.cpp:171: error: 'struct x264_param_t::<anonymous>' has no member named 'b_cbr'

I fount video_x264.cpp in /server , and commented out line 171.  It compiled, and I used sudo checkinstall to install it.  Works fine.  I now have mp4live with x264 on feisty athlon 64 / amd64 or x86_64 , whatever you want to call it.  mpeg4ip is now installed with a deb.  I guess if I can run checkinstall, I should be able to make a deb for it.  Haven't gone there yet, but there should be enough info here for someone to replicate what I have done.

---

