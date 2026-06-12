---
title: "fuppes error whe3n traqnscoding .mpg files to xbox"
date: 2010-02-21
forum: Multimedia Software
---

### Post by neill64 on 2010-02-21
has anyone gone .mpg transcoding working on fuppes, i have a large collection of .mpg files that i want to serve from my ubuntu 9.10 server using fuppes 661.

i can play the files on my ps3 and all works fine but when i try to play them on my xbox 360 with fuppes in debug mode i get a message saying "connection to my computer was lost" status code "53-C00DF238" and on my fuppes console i get  the following :-

== lib/HTTP/HTTPMessage.cpp (750) :: Sun Feb 21 17:01:25 2010 ==
init transcoding failed :: /home/neill/Videos/ap1.mpg


below are various bits of config files,


my xbox fuppes.cfg has :-

    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>
            <file ext="mpg">
                  <type>VIDEO_ITEM</type>
                  <mime_type>video/mpeg</mime_type>
                  <transcode enabled="true">
                  <transcoder>ffmpeg</transcoder>
                  <ext>wmv</ext>
                  <mime_type>video/x-ms-wmv</mime_type>
                  <video_codec>wmv2</video_codec>
                  <audio_codec>wmav1</audio_codec>           
                  <video_bitrate>180000</video_bitrate>
                  <audio_bitrate>128000</audio_bitrate>
                  </transcode>
            </file>
        </file_settings>
    <description_values>
    <friendly_name>Neills %v : 1 : Windows Media Connect</friendly_name>
    <model_name>Windows Media Connect compatible (%s)</model_name>
    <model_number>2.0</model_number>
    </description_values> 
    </device>
  </device_settings>
</fuppes_config>

=======================================================

if i runj a configure in ffmpeg i get 

neill@ubuntu:~/ffmpeg$ ./configure
install prefix            /usr/local
source path               /home/neill/ffmpeg
C compiler                gcc
.align is power-of-two    no
ARCH                      x86 (generic)
big-endian                no
runtime cpu detection     no
yasm                      yes
MMX enabled               yes
MMX2 enabled              yes
3DNow! enabled            yes
3DNow! extended enabled   yes
SSE enabled               yes
SSSE3 enabled             yes
CMOV enabled              no
CMOV is fast              no
EBX available             yes
EBP available             no
10 operands supported     yes
gprof enabled             no
debug symbols             yes
strip symbols             yes
optimizations             yes
static                    yes
shared                    no
postprocessing support    no
new filter support        no
filters using lavformat   no
network support           yes
threading support         no
SDL support               yes
Sun medialib support      no
AVISynth enabled          no
libdc1394 support         no
libdirac enabled          no
libfaac enabled           no
libfaad enabled           no
libfaad dlopened          no
libgsm enabled            no
libmp3lame enabled        no
libnut enabled            no
libopencore-amrnb support no
libopencore-amrwb support no
libopenjpeg enabled       no
libschroedinger enabled   no
libspeex enabled          no
libtheora enabled         no
libvorbis enabled         no
libx264 enabled           no
libxvid enabled           no
zlib enabled              yes
bzlib enabled             no

Enabled decoders:
aac            eacmv            pcm_alaw
aasc            eamad            pcm_bluray
ac3            eatgq            pcm_dvd
adpcm_4xm        eatgv            pcm_f32be
adpcm_adx        eatqi            pcm_f32le
adpcm_ct        eightbps        pcm_f64be
adpcm_ea        eightsvx_exp        pcm_f64le
adpcm_ea_maxis_xa    eightsvx_fib        pcm_mulaw
adpcm_ea_r1        escape124        pcm_s16be
adpcm_ea_r2        ffv1            pcm_s16le
adpcm_ea_r3        ffvhuff            pcm_s16le_planar
adpcm_ea_xas        flac            pcm_s24be
adpcm_g726        flashsv            pcm_s24daud
adpcm_ima_amv        flic            pcm_s24le
adpcm_ima_dk3        flv            pcm_s32be
adpcm_ima_dk4        fourxm            pcm_s32le
adpcm_ima_ea_eacs    fraps            pcm_s8
adpcm_ima_ea_sead    frwu            pcm_u16be
adpcm_ima_iss        gif            pcm_u16le
adpcm_ima_qt        h261            pcm_u24be
adpcm_ima_smjpeg    h263            pcm_u24le
adpcm_ima_wav        h263i            pcm_u32be
adpcm_ima_ws        h264            pcm_u32le
adpcm_ms        huffyuv            pcm_u8
adpcm_sbpro_2        idcin            pcm_zork
adpcm_sbpro_3        iff_byterun1        pcx
adpcm_sbpro_4        iff_ilbm        pgm
adpcm_swf        imc            pgmyuv
adpcm_thp        indeo2            pgssub
adpcm_xa        indeo3            png
adpcm_yamaha        indeo5            ppm
alac            interplay_dpcm        ptx
als            interplay_video        qcelp
amv            jpegls            qdm2
anm            kmvc            qdraw
ape            loco            qpeg
asv1            mace3            qtrle
asv2            mace6            r210
atrac1            mdec            ra_144
atrac3            mimic            ra_288
aura            mjpeg            rawvideo
aura2            mjpegb            rl2
avs            mlp            roq
bethsoftvid        mmvideo            roq_dpcm
bfi            motionpixels        rpza
binkaudio_dct        mp1            rv10
binkaudio_rdft        mp2            rv20
bmp            mp3            rv30
c93            mp3adu            rv40
cavs            mp3on4            sgi
cdgraphics        mpc7            shorten
cinepak            mpc8            sipr
cljr            mpeg1video        smackaud
cook            mpeg2video        smacker
cscd            mpeg4            smc
cyuv            mpegvideo        snow
dca            msmpeg4v1        sol_dpcm
dnxhd            msmpeg4v2        sonic
dpx            msmpeg4v3        sp5x
dsicinaudio        msrle            sunrast
dsicinvideo        msvideo1        svq1
dvbsub            mszh            svq3
dvdsub            nellymoser        targa
dvvideo            nuv            theora
dxa            pam            thp
eac3            pbm            tiertexseqvideo
tiff            vc1            wmav1
tmv            vcr1            wmav2
truehd            vmdaudio        wmavoice
truemotion1        vmdvideo        wmv1
truemotion2        vmnc            wmv2
truespeech        vorbis            wmv3
tscc            vp3            wnv1
tta            vp5            ws_snd1
twinvq            vp6            xan_dpcm
txd            vp6a            xan_wc3
ulti            vp6f            xl
v210            vqa            xsub
v210x            wavpack            zlib
vb            wmapro            zmbv

Enabled encoders:
aac            mp2            pcm_u8
ac3            mpeg1video        pcm_zork
adpcm_adx        mpeg2video        pcx
adpcm_g726        mpeg4            pgm
adpcm_ima_qt        msmpeg4v1        pgmyuv
adpcm_ima_wav        msmpeg4v2        png
adpcm_ms        msmpeg4v3        ppm
adpcm_swf        nellymoser        qtrle
adpcm_yamaha        pam            rawvideo
alac            pbm            roq
asv1            pcm_alaw        roq_dpcm
asv2            pcm_f32be        rv10
bmp            pcm_f32le        rv20
dnxhd            pcm_f64be        sgi
dvbsub            pcm_f64le        snow
dvdsub            pcm_mulaw        sonic
dvvideo            pcm_s16be        sonic_ls
ffv1            pcm_s16le        svq1
ffvhuff            pcm_s24be        targa
flac            pcm_s24daud        tiff
flashsv            pcm_s24le        v210
flv            pcm_s32be        vorbis
gif            pcm_s32le        wmav1
h261            pcm_s8            wmav2
h263            pcm_u16be        wmv1
h263p            pcm_u16le        wmv2
huffyuv            pcm_u24be        xsub
jpegls            pcm_u24le        zlib
ljpeg            pcm_u32be        zmbv
mjpeg            pcm_u32le

Enabled hwaccels:

Enabled parsers:
aac            dvdsub            mpeg4video
ac3            h261            mpegaudio
cavsvideo        h263            mpegvideo
dca            h264            pnm
dirac            mjpeg            vc1
dnxhd            mlp            vp3
dvbsub

Enabled demuxers:
aac            image2pipe        pcm_u16le
ac3            ingenient        pcm_u24be
aea            ipmovie            pcm_u24le
aiff            iss            pcm_u32be
amr            iv8            pcm_u32le
anm            lmlm4            pcm_u8
apc            m4v            pva
ape            matroska        qcp
asf            mjpeg            r3d
***            mlp            rawvideo
au            mm            rl2
avi            mmf            rm
avs            mov            roq
bethsoftvid        mp3            rpl
bfi            mpc            rtsp
bink            mpc8            sdp
c93            mpegps            segafilm
caf            mpegts            shorten
cavsvideo        mpegtsraw        siff
cdg            mpegvideo        smacker
daud            msnwc_tcp        sol
dirac            mtv            sox
dnxhd            mvi            str
dsicin            mxf            swf
dts            nc            thp
dv            nsv            tiertexseq
dxa            nut            tmv
ea            nuv            truehd
ea_cdata        ogg            tta
eac3            oma            txd
ffm            pcm_alaw        vc1
filmstrip        pcm_f32be        vc1t
flac            pcm_f32le        vmd
flic            pcm_f64be        voc
flv            pcm_f64le        vqf
fourxm            pcm_mulaw        w64
gsm            pcm_s16be        wav
gxf            pcm_s16le        wc3
h261            pcm_s24be        wsaud
h263            pcm_s24le        wsvqa
h264            pcm_s32be        wv
idcin            pcm_s32le        xa
iff            pcm_s8            yuv4mpegpipe
image2            pcm_u16be

Enabled muxers:
ac3            m4v            pcm_s16be
adts            matroska        pcm_s16le
aiff            matroska_audio        pcm_s24be
amr            mjpeg            pcm_s24le
asf            mlp            pcm_s32be
asf_stream        mmf            pcm_s32le
***            mov            pcm_s8
au            mp2            pcm_u16be
avi            mp3            pcm_u16le
avm2            mp4            pcm_u24be
crc            mpeg1system        pcm_u24le
daud            mpeg1vcd        pcm_u32be
dirac            mpeg1video        pcm_u32le
dnxhd            mpeg2dvd        pcm_u8
dts            mpeg2svcd        psp
dv            mpeg2video        rawvideo
eac3            mpeg2vob        rm
ffm            mpegts            roq
filmstrip        mpjpeg            rtp
flac            mxf            sox
flv            mxf_d10            spdif
framecrc        null            swf
gif            nut            tg2
gxf            ogg            tgp
h261            pcm_alaw        truehd
h263            pcm_f32be        vc1t
h264            pcm_f32le        voc
image2            pcm_f64be        wav
image2pipe        pcm_f64le        yuv4mpegpipe
ipod            pcm_mulaw

Enabled protocols:
concat            http            rtp
file            pipe            tcp
gopher            rtmp            udp

Enabled filters:
crop            null            scale
format            nullsink        slicify
noformat        nullsrc            vflip

Enabled bsfs:
aac_adtstoasc        mjpega_dump_header    noise
dump_extradata        mov2textsub        remove_extradata
h264_mp4toannexb    mp3_header_compress    text2movsub
imx_dump_header        mp3_header_decompress

Enabled indevs:
alsa            oss            v4l2
dv1394            v4l

Enabled outdevs:
alsa            oss

License: LGPL version 2.1 or later
Creating config.mak and config.h...
libavutil/avconfig.h is unchanged


====================================================

and a configure in fuppes i get
CONFIGURATION SUMMARY

  audio transcoding plugins
    encoder:
      lame       : no
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : no
      mpc        : no
      flac       : no
      faad       : no (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg             : enabled

  image conversion/rescaling plugins
    ImageMagick        : disabled (Wand C-API)

  audio metadata extraction plugins
    taglib             : disabled (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2      : disabled (mp4/m4a)

  image metadata extraction plugins
    Exiv2              : disabled
    ImageMagick        : disabled (Wand C-API)
    simage             : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat        : enabled
    ffmpegthumbnailer  : disabled

  miscellaneous
    iconv              : enabled (charset conversion)
    uuid               : disabled
    inotify            : enabled

Thanks for using fuppes
please report bugs

---

