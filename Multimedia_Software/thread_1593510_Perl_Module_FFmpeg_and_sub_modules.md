---
title: "Perl Module FFmpeg and sub modules"
date: 2010-10-11
forum: Multimedia Software
---

### Post by cbxk1xg on 2010-10-11
Hello,

I'm running 10.4 LTS Desktop on a XEN-Machine as a VM. Gnome is disabled. I'm currently trying to install the Perl module FFmpeg. It is kind of a API for ffmpeg in Perl. I managed to compile and install ffmpeg from source, including all the dependencies like codecs and what not. FFmpeg is running.

Unfortunatelly I'm not able to install the Perl Module. Here is what I used to get, when I try to install the module in the cpan-shell. And by the way, if I install it from the source by "perl Makefile.Pl, make test, etc..." I get exactly the same result.

```
root@dev2:~# cpan

cpan shell -- CPAN exploration and modules installation (v1.9402)
Enter 'h' for help.

cpan[1]> install FFmpeg                                                                                                                                                                                                                     
CPAN: Storable loaded ok (v2.15)
Going to read '/root/.cpan/Metadata'
  Database was generated on Mon, 11 Oct 2010 10:29:58 GMT
Running install for module 'FFmpeg'
Running make for A/AL/ALLENDAY/FFmpeg-6036.tar.gz
CPAN: Digest::SHA loaded ok (v5.48)
CPAN: Compress::Zlib loaded ok (v2.03)
Checksum for /root/.cpan/sources/authors/id/A/AL/ALLENDAY/FFmpeg-6036.tar.gz ok
Scanning cache /root/.cpan/build for sizes
............................................................----------------DONE
DEL(1/4): /root/.cpan/build/FFmpeg-6036-C06E7P 
CPAN: YAML loaded ok (v0.72)
DEL(2/4): /root/.cpan/build/FFmpeg-6036-C06E7P.yml 
DEL(3/4): /root/.cpan/build/Time-Piece-1.20-EbS4Rt 
DEL(4/4): /root/.cpan/build/Time-Piece-1.20-EbS4Rt.yml 
CPAN: Archive::Tar loaded ok (v1.68)
FFmpeg-6036/
FFmpeg-6036/t/
FFmpeg-6036/t/11.transcode.t
FFmpeg-6036/t/07.m2v.t
FFmpeg-6036/t/04.mov.t
FFmpeg-6036/t/03.avi.t
FFmpeg-6036/t/02.asf.t
FFmpeg-6036/t/06.mp3.t
FFmpeg-6036/t/05.mp2.t
FFmpeg-6036/t/01.FFmpeg.t
FFmpeg-6036/t/08.capture.t
FFmpeg-6036/t/09.http.t
FFmpeg-6036/t/10.perf.t
FFmpeg-6036/eg/
FFmpeg-6036/eg/t1.mov
FFmpeg-6036/eg/t1.avi
FFmpeg-6036/eg/t1.mpg
FFmpeg-6036/eg/t1.mp2
FFmpeg-6036/eg/t1.mp3
FFmpeg-6036/eg/t1.asf
FFmpeg-6036/eg/t1.m2v
FFmpeg-6036/eg/t2.mov
FFmpeg-6036/eg/t2.avi
FFmpeg-6036/eg/t2.mpg
FFmpeg-6036/eg/t2.asf
FFmpeg-6036/eg/t3.asf
FFmpeg-6036/FFmpeg.pm
FFmpeg-6036/FFmpeg.xs
FFmpeg-6036/ffmpeg-6036.c
FFmpeg-6036/Makefile.PL
FFmpeg-6036/ffmpeg.h
FFmpeg-6036/Changes
FFmpeg-6036/FFmpeg/
FFmpeg-6036/FFmpeg/StreamGroup.pm
FFmpeg-6036/FFmpeg/Stream.pm
FFmpeg-6036/FFmpeg/FileFormat.pm
FFmpeg-6036/FFmpeg/Codec.pm
FFmpeg-6036/FFmpeg/ImageFormat.pm
FFmpeg-6036/FFmpeg/Stream/
FFmpeg-6036/FFmpeg/Stream/Unknown.pm
FFmpeg-6036/FFmpeg/Stream/Data.pm
FFmpeg-6036/FFmpeg/Stream/Audio.pm
FFmpeg-6036/FFmpeg/Stream/Video.pm
FFmpeg-6036/MANIFEST
FFmpeg-6036/META.yml
FFmpeg-6036/ffmpeg-6036.c.orig
FFmpeg-6036/README
FFmpeg-6036/config-6036.h
CPAN: File::Temp loaded ok (v0.22)

  CPAN.pm: Going to build A/AL/ALLENDAY/FFmpeg-6036.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for FFmpeg
cp FFmpeg/Stream/Audio.pm blib/lib/FFmpeg/Stream/Audio.pm
cp FFmpeg/FileFormat.pm blib/lib/FFmpeg/FileFormat.pm
cp FFmpeg/Codec.pm blib/lib/FFmpeg/Codec.pm
cp FFmpeg/Stream/Data.pm blib/lib/FFmpeg/Stream/Data.pm
cp FFmpeg/Stream.pm blib/lib/FFmpeg/Stream.pm
cp FFmpeg.pm blib/lib/FFmpeg.pm
cp FFmpeg/StreamGroup.pm blib/lib/FFmpeg/StreamGroup.pm
cp FFmpeg/Stream/Video.pm blib/lib/FFmpeg/Stream/Video.pm
cp FFmpeg/ImageFormat.pm blib/lib/FFmpeg/ImageFormat.pm
cp FFmpeg/Stream/Unknown.pm blib/lib/FFmpeg/Stream/Unknown.pm
/usr/bin/perl /usr/local/share/perl/5.8.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap  FFmpeg.xs > FFmpeg.xsc && mv FFmpeg.xsc FFmpeg.c
cc -c  -I. -I/usr/local/bin -I/usr/local/bin/libavutil -I/usr/local/bin/libavcodec -I/usr/local/bin/libavformat -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2  -DPERL_EXTMALLOC_DEF -Dmalloc=Perl_malloc -Dfree=Perl_mfree -Drealloc=Perl_realloc -Dcalloc=Perl_calloc -DVERSION=\"6036\" -DXS_VERSION=\"6036\" -fPIC "-I/usr/lib/perl/5.8/CORE"  -O FFmpeg.c
In Datei, eingefügt von ffmpeg.h:2,
                 von FFmpeg.xs:16:
./ffmpeg-6036.c:21:22: Fehler: avformat.h: No such file or directory
./ffmpeg-6036.c:22:21: Fehler: swscale.h: No such file or directory
./ffmpeg-6036.c:23:23: Fehler: framehook.h: No such file or directory
./ffmpeg-6036.c:24:21: Fehler: dsputil.h: No such file or directory
./ffmpeg-6036.c:25:17: Fehler: opt.h: No such file or directory
./ffmpeg-6036.c:44:21: Fehler: version.h: No such file or directory
./ffmpeg-6036.c:45:22: Fehler: cmdutils.h: No such file or directory
In file included from ffmpeg.h:2,
                 from FFmpeg.xs:16:
./ffmpeg-6036.c:68: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »options«
./ffmpeg-6036.c:76: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »*« token
./ffmpeg-6036.c:80: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »*« token
./ffmpeg-6036.c:89: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »*« token
./ffmpeg-6036.c:90: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »*« token
./ffmpeg-6036.c:91: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »*« token
./ffmpeg-6036.c:95: Fehler: Variable »frame_pix_fmt« hat Initialisierung, aber unvollständigen Typ
./ffmpeg-6036.c:95: Fehler: »PIX_FMT_NONE« ist hier nicht deklariert (nicht in einer Funktion)
./ffmpeg-6036.c:113: Fehler: »FF_QP2LAMBDA« ist hier nicht deklariert (nicht in einer Funktion)
./ffmpeg-6036.c:139: Fehler: »FF_DEFAULT_QUANT_BIAS« ist hier nicht deklariert (nicht in einer Funktion)
./ffmpeg-6036.c:141: Fehler: »ME_EPZS« ist hier nicht deklariert (nicht in einer Funktion)
./ffmpeg-6036.c:144: Fehler: »CODEC_ID_NONE« ist hier nicht deklariert (nicht in einer Funktion)
./ffmpeg-6036.c:150: Fehler: »FF_BUG_AUTODETECT« ist hier nicht deklariert (nicht in einer Funktion)
./ffmpeg-6036.c:164: Fehler: »AVFMT_NOOUTPUTLOOP« ist hier nicht deklariert (nicht in einer Funktion)
./ffmpeg-6036.c:250: Fehler: »SWS_BICUBIC« ist hier nicht deklariert (nicht in einer Funktion)
./ffmpeg-6036.c:254: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »*« token
./ffmpeg-6036.c:256: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »*« token
./ffmpeg-6036.c:257: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »*« token
./ffmpeg-6036.c:258: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »*« token
./ffmpeg-6036.c:268: Fehler: expected specifier-qualifier-list before »AVStream«
./ffmpeg-6036.c:302: Fehler: expected specifier-qualifier-list before »AVStream«
./ffmpeg-6036.c:423: Fehler: expected »)« before »*« token
./ffmpeg-6036.c: In Funktion »get_sync_ipts«:
./ffmpeg-6036.c:451: Fehler: »AVOutputStream« hat kein Element namens »sync_ist«
./ffmpeg-6036.c:452: Fehler: »AVInputStream« hat kein Element namens »pts«
./ffmpeg-6036.c:452: Fehler: »AV_TIME_BASE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:452: Fehler: (Jeder nicht deklarierte Bezeichner wird nur einmal aufgeführt
./ffmpeg-6036.c:452: Fehler: für jede Funktion in der er auftritt.)
./ffmpeg-6036.c: Auf höchster Ebene:
./ffmpeg-6036.c:455: Fehler: expected »)« before »*« token
./ffmpeg-6036.c:476: Fehler: expected »)« before »*« token
./ffmpeg-6036.c:625: Fehler: expected declaration specifiers or »...« before »AVPicture«
./ffmpeg-6036.c: In Funktion »pre_process_video_frame«:
./ffmpeg-6036.c:627: Fehler: »AVCodecContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:627: Fehler: »dec« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:628: Fehler: »AVPicture« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:628: Fehler: »picture2« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:629: Fehler: expected »;« before »picture_tmp«
./ffmpeg-6036.c:632: Fehler: »AVInputStream« hat kein Element namens »st«
./ffmpeg-6036.c:640: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
./ffmpeg-6036.c:644: Fehler: »picture_tmp« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:648: Fehler: »picture« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: Auf höchster Ebene:
./ffmpeg-6036.c:672: Fehler: expected »)« before »*« token
./ffmpeg-6036.c:727: Fehler: expected »)« before »*« token
./ffmpeg-6036.c:901: Fehler: expected »)« before »*« token
./ffmpeg-6036.c:948: Fehler: expected »)« before »*« token
./ffmpeg-6036.c:1068: Fehler: expected »;«, »,« or »)« before »*« token
./ffmpeg-6036.c:1401: Fehler: expected »)« before »*« token
./ffmpeg-6036.c: In Funktion »opt_image_format«:
./ffmpeg-6036.c:2091: Fehler: »AVImageFormat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2091: Fehler: »f« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2093: Fehler: »first_image_format« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2101: Fehler: »image_format« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_format«:
./ffmpeg-6036.c:2113: Fehler: »file_iformat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2114: Fehler: »file_oformat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_frame_pix_fmt«:
./ffmpeg-6036.c:2359: Fehler: »frame_pix_fmt« hat unvollständigen Typ
./ffmpeg-6036.c: In Funktion »opt_b_frames«:
./ffmpeg-6036.c:2393: Fehler: »FF_MAX_B_FRAMES« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_mb_lmin«:
./ffmpeg-6036.c:2461: Fehler: »FF_LAMBDA_MAX« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_mb_lmax«:
./ffmpeg-6036.c:2471: Fehler: »FF_LAMBDA_MAX« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_video_device«:
./ffmpeg-6036.c:2583: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
./ffmpeg-6036.c: In Funktion »opt_grab_device«:
./ffmpeg-6036.c:2588: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
./ffmpeg-6036.c: In Funktion »opt_video_standard«:
./ffmpeg-6036.c:2598: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
./ffmpeg-6036.c: In Funktion »opt_audio_device«:
./ffmpeg-6036.c:2603: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
./ffmpeg-6036.c: In Funktion »opt_codec«:
./ffmpeg-6036.c:2609: Fehler: »AVCodec« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2609: Fehler: »p« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2614: Fehler: »first_avcodec« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_audio_codec«:
./ffmpeg-6036.c:2631: Fehler: »CODEC_TYPE_AUDIO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »add_frame_hooker«:
./ffmpeg-6036.c:2657: Warnung: Initialisierung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
./ffmpeg-6036.c: In Funktion »opt_video_codec«:
./ffmpeg-6036.c:2704: Fehler: »CODEC_TYPE_VIDEO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_subtitle_codec«:
./ffmpeg-6036.c:2709: Fehler: »CODEC_TYPE_SUBTITLE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_input_file«:
./ffmpeg-6036.c:2774: Fehler: »AVFormatContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2774: Fehler: »ic« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2775: Fehler: »AVFormatParameters« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2775: Fehler: expected »;« before »params«
./ffmpeg-6036.c:2786: Fehler: »ap« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2793: Fehler: »image_format« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2801: Fehler: »CODEC_ID_PGMYUV« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2804: Fehler: »file_iformat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2813: Fehler: »AVFMT_FLAG_GENPTS« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2825: Fehler: »AV_NOPTS_VALUE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2830: Fehler: »AVSEEK_FLAG_BACKWARD« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2833: Fehler: »AV_TIME_BASE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2842: Fehler: »AVCodecContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2842: Fehler: »enc« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2849: Fehler: »CODEC_TYPE_AUDIO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2851: Fehler: »AVOption« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2851: Fehler: »opt« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2852: Fehler: »avctx_opts« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2853: Fehler: »AV_OPT_FLAG_AUDIO_PARAM« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2853: Fehler: »AV_OPT_FLAG_DECODING_PARAM« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2860: Fehler: »AVDISCARD_ALL« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2862: Fehler: »CODEC_TYPE_VIDEO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2866: Fehler: »AV_OPT_FLAG_VIDEO_PARAM« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2872: Fehler: »frame_pix_fmt« hat unvollständigen Typ
./ffmpeg-6036.c:2876: Fehler: »CODEC_FLAG_EMU_EDGE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2878: Fehler: »FF_DEBUG_MV« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2898: Fehler: »CODEC_TYPE_DATA« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2900: Fehler: »CODEC_TYPE_SUBTITLE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2902: Fehler: »CODEC_TYPE_UNKNOWN« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2909: Fehler: »input_files« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2917: Fehler: »file_oformat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_grab«:
./ffmpeg-6036.c:2928: Fehler: »file_iformat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »check_audio_video_inputs«:
./ffmpeg-6036.c:2935: Fehler: »AVFormatContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2935: Fehler: »ic« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2940: Fehler: »input_files« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2942: Fehler: »AVCodecContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2942: Fehler: »enc« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2944: Fehler: »CODEC_TYPE_AUDIO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2947: Fehler: »CODEC_TYPE_VIDEO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2950: Fehler: »CODEC_TYPE_DATA« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2951: Fehler: »CODEC_TYPE_UNKNOWN« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:2952: Fehler: »CODEC_TYPE_SUBTITLE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: Auf höchster Ebene:
./ffmpeg-6036.c:2963: Fehler: expected »)« before »*« token
./ffmpeg-6036.c:3165: Fehler: expected »)« before »*« token
./ffmpeg-6036.c: In Funktion »opt_new_subtitle_stream«:
./ffmpeg-6036.c:3243: Fehler: »AVFormatContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3243: Fehler: »oc« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3244: Fehler: »AVStream« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3244: Fehler: »st« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3245: Fehler: »AVCodecContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3245: Fehler: »subtitle_enc« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3252: Fehler: »output_files« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3261: Fehler: »CODEC_TYPE_SUBTITLE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3266: Fehler: »AVOption« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3266: Fehler: »opt« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3267: Fehler: »avctx_opts« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3268: Fehler: »AV_OPT_FLAG_SUBTITLE_PARAM« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3268: Fehler: »AV_OPT_FLAG_ENCODING_PARAM« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_new_audio_stream«:
./ffmpeg-6036.c:3286: Fehler: »AVFormatContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3286: Fehler: »oc« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3291: Fehler: »output_files« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_new_video_stream«:
./ffmpeg-6036.c:3297: Fehler: »AVFormatContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3297: Fehler: »oc« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3302: Fehler: »output_files« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_output_file«:
./ffmpeg-6036.c:3308: Fehler: »AVFormatContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3308: Fehler: »oc« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3310: Fehler: »AVFormatParameters« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3310: Fehler: expected »;« before »params«
./ffmpeg-6036.c:3317: Fehler: »file_oformat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3384: Fehler: »output_files« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3387: Fehler: »AVFMT_NEEDNUMBER« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3389: Fehler: »AVERROR_NUMEXPECTED« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3394: Fehler: »AVFMT_NOFILE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3419: Fehler: »URL_WRONLY« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3425: Fehler: »ap« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3426: Fehler: »image_format« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3435: Fehler: »AV_TIME_BASE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3441: Fehler: »file_iformat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »prepare_grab«:
./ffmpeg-6036.c:3449: Fehler: »AVFormatContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3449: Fehler: »oc« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3450: Fehler: »ic« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3451: Fehler: »AVFormatParameters« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3451: Fehler: expected »;« before »vp1«
./ffmpeg-6036.c:3452: Fehler: expected »;« before »ap1«
./ffmpeg-6036.c:3457: Fehler: »ap« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3458: Fehler: »vp« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3461: Fehler: »output_files« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3463: Fehler: »AVCodecContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3463: Fehler: »enc« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3465: Fehler: »CODEC_TYPE_AUDIO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3472: Fehler: »CODEC_TYPE_VIDEO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3499: Fehler: »AVInputFormat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3499: Fehler: »fmt1« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3511: Fehler: »AVFMTCTX_NOHEADER« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3518: Fehler: »input_files« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »show_formats«:
./ffmpeg-6036.c:3573: Fehler: »AVInputFormat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3573: Fehler: »ifmt« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3574: Fehler: »AVOutputFormat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3574: Fehler: »ofmt« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3575: Fehler: »AVImageFormat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3575: Fehler: »image_fmt« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3576: Fehler: »URLProtocol« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3576: Fehler: »up« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3577: Fehler: »AVCodec« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3577: Fehler: »p« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3577: Fehler: »p2« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3588: Fehler: »first_oformat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3596: Fehler: »first_iformat« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3620: Fehler: »first_image_format« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3640: Fehler: »first_avcodec« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3657: Fehler: »CODEC_TYPE_VIDEO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3660: Fehler: »CODEC_TYPE_AUDIO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3663: Fehler: »CODEC_TYPE_SUBTITLE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3675: Fehler: »CODEC_CAP_DRAW_HORIZ_BAND« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3676: Fehler: »CODEC_CAP_DR1« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3677: Fehler: »CODEC_CAP_TRUNCATED« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3686: Fehler: »first_protocol« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3695: Fehler: »ME_ZERO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3697: Fehler: »ME_FULL« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_inter_matrix«:
./ffmpeg-6036.c:3732: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
./ffmpeg-6036.c: In Funktion »opt_intra_matrix«:
./ffmpeg-6036.c:3738: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
./ffmpeg-6036.c: In Funktion »opt_target«:
./ffmpeg-6036.c:3769: Fehler: »input_files« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3770: Fehler: »AVCodecContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3770: Fehler: »c« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3771: Fehler: »CODEC_TYPE_VIDEO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_video_bsf«:
./ffmpeg-6036.c:3888: Fehler: »AVBitStreamFilterContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3888: Fehler: »bsfc« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3889: Fehler: »bsfp« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3896: Fehler: »video_bitstream_filters« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »opt_audio_bsf«:
./ffmpeg-6036.c:3906: Fehler: »AVBitStreamFilterContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3906: Fehler: »bsfc« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3907: Fehler: »bsfp« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3914: Fehler: »audio_bitstream_filters« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »show_version«:
./ffmpeg-6036.c:3924: Fehler: expected »)« before »FFMPEG_VERSION«
./ffmpeg-6036.c: In Funktion »opt_default«:
./ffmpeg-6036.c:3933: Fehler: »AVOption« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3933: Fehler: »o« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3933: Fehler: »avctx_opts« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3940: Warnung: Zuweisung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
./ffmpeg-6036.c:3944: Fehler: »CODEC_FLAG_BITEXACT« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:3948: Fehler: »AV_LOG_DEBUG« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: Auf höchster Ebene:
./ffmpeg-6036.c:3952: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »options«
./ffmpeg-6036.c: In Funktion »show_banner«:
./ffmpeg-6036.c:4115: Fehler: expected »)« before »FFMPEG_VERSION«
./ffmpeg-6036.c:4117: Fehler: expected »)« before »AV_STRINGIFY«
./ffmpeg-6036.c:4118: Fehler: expected »)« before »AV_STRINGIFY«
./ffmpeg-6036.c:4119: Fehler: expected »)« before »AV_STRINGIFY«
./ffmpeg-6036.c: In Funktion »show_help«:
./ffmpeg-6036.c:4173: Fehler: »options« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4174: Fehler: »OPT_EXPERT« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4174: Fehler: »OPT_AUDIO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4174: Fehler: »OPT_VIDEO« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4176: Fehler: »OPT_GRAB« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4188: Fehler: »OPT_SUBTITLE« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4196: Fehler: »avctx_opts« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c: In Funktion »main«:
./ffmpeg-6036.c:4213: Fehler: »avctx_opts« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4221: Fehler: »options« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4235: Fehler: »output_files« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4235: Fehler: »input_files« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4245: Fehler: »AVFormatContext« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4245: Fehler: »s« nicht deklariert (erste Benutzung in dieser Funktion)
./ffmpeg-6036.c:4247: Fehler: »AVFMT_NOFILE« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs: Auf höchster Ebene:
FFmpeg.xs:19: Fehler: expected »;«, »,« or »)« before »*« token
FFmpeg.xs:20: Warnung: In Konflikt stehende Typen für »print_error«
./ffmpeg-6036.c:2806: Warnung: Vorherige implizite Deklaration von »print_error« war hier
FFmpeg.xs:21: Fehler: expected »;«, »,« or »)« before »*« token
FFmpeg.xs: In Funktion »XS_FFmpeg__run_ffmpeg«:
FFmpeg.xs:52: Fehler: »output_files« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:52: Fehler: »input_files« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs: In Funktion »XS_FFmpeg__image_formats«:
FFmpeg.xs:355: Fehler: »AVInputFormat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:355: Fehler: »ifmt« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:356: Fehler: »AVOutputFormat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:356: Fehler: »ofmt« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:357: Fehler: »AVImageFormat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:357: Fehler: »image_fmt« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:358: Fehler: »URLProtocol« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:358: Fehler: »up« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:359: Fehler: »AVCodec« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:359: Fehler: »p« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:359: Fehler: »p2« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:364: Fehler: »first_image_format« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs: In Funktion »XS_FFmpeg__file_formats«:
FFmpeg.xs:388: Fehler: »AVInputFormat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:388: Fehler: »ifmt« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:389: Fehler: »AVOutputFormat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:389: Fehler: »ofmt« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:390: Fehler: »AVImageFormat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:390: Fehler: »image_fmt« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:391: Fehler: »URLProtocol« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:391: Fehler: »up« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:392: Fehler: »AVCodec« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:392: Fehler: »p« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:392: Fehler: »p2« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:408: Fehler: »first_oformat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:420: Fehler: »first_iformat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs: In Funktion »XS_FFmpeg__init_AVFormatContext«:
FFmpeg.xs:470: Fehler: »AVFormatContext« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs: In Funktion »XS_FFmpeg__free_AVFormatContext«:
FFmpeg.xs:483: Fehler: »AVFormatContext« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:483: Fehler: »ic« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:483: Fehler: expected expression before »)« token
FFmpeg.xs: In Funktion »XS_FFmpeg__init_streamgroup«:
FFmpeg.xs:501: Fehler: »AVFormatContext« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:501: Fehler: »ic« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:501: Fehler: expected expression before »)« token
FFmpeg.xs:502: Fehler: »AVFormatParameters« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:502: Fehler: expected »;« before »params«
FFmpeg.xs:506: Fehler: »ap« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:506: Fehler: »image_format« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:508: Fehler: »file_iformat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:541: Fehler: »AV_NOPTS_VALUE« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:559: Fehler: »AV_TIME_BASE« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:566: Fehler: »AVStream« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:566: Fehler: »st« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:575: Fehler: »AVCodecContext« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:575: Fehler: »ctx« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:576: Fehler: »AVCodec« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:576: Fehler: »codec« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs: In Funktion »XS_FFmpeg__codecs«:
FFmpeg.xs:631: Fehler: »AVInputFormat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:631: Fehler: »ifmt« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:632: Fehler: »AVOutputFormat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:632: Fehler: »ofmt« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:633: Fehler: »AVImageFormat« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:633: Fehler: »image_fmt« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:634: Fehler: »URLProtocol« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:634: Fehler: »up« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:635: Fehler: »AVCodec« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:635: Fehler: »p« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:635: Fehler: »p2« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:648: Fehler: »first_avcodec« nicht deklariert (erste Benutzung in dieser Funktion)
FFmpeg.xs:670: Fehler: »CODEC_TYPE_AUDIO« nicht deklariert (erste Benutzung in dieser Funktion)
make: *** [FFmpeg.o] Fehler 1
  ALLENDAY/FFmpeg-6036.tar.gz
  /usr/bin/make -- NOT OK
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible

cpan[2]>
```

---

### Post by cbxk1xg on 2010-10-11
anyone?

---

### Post by cbxk1xg on 2010-10-14
This is stil UNsolved. Why did someone changed it to solved???

---

