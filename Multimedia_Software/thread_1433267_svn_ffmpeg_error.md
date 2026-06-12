---
title: "svn ffmpeg error"
date: 2010-03-18
forum: Multimedia Software
---

### Post by Mia1990 on 2010-03-18
Trying to upgrade to the newest svn ffmpeg and i am getting errors here is the terminal output.
l> ibavcodec/utils.c: In function ‘avcodec_encode_audio’:
libavcodec/utils.c:539: warning: passing argument 4 of ‘avctx->codec->encode’ discards qualifiers from pointer target type
libavcodec/utils.c:539: note: expected ‘void *’ but argument is of type ‘const short int *’
libavcodec/utils.c: In function ‘avcodec_encode_video’:
libavcodec/utils.c:556: warning: passing argument 4 of ‘avctx->codec->encode’ discards qualifiers from pointer target type
libavcodec/utils.c:556: note: expected ‘void *’ but argument is of type ‘const struct AVFrame *’
libavcodec/utils.c: In function ‘avcodec_encode_subtitle’:
libavcodec/utils.c:575: warning: passing argument 4 of ‘avctx->codec->encode’ discards qualifiers from pointer target type
libavcodec/utils.c:575: note: expected ‘void *’ but argument is of type ‘const struct AVSubtitle *’
libavcodec/utils.c: In function ‘avcodec_decode_video’:
libavcodec/utils.c:587: warning: assignment discards qualifiers from pointer target type
libavcodec/utils.c: In function ‘avcodec_decode_audio2’:
libavcodec/utils.c:626: warning: assignment discards qualifiers from pointer target type
libavcodec/utils.c: In function ‘avcodec_decode_subtitle’:
libavcodec/utils.c:667: warning: assignment discards qualifiers from pointer target type
libavcodec/utils.c: In function ‘av_parse_video_frame_size’:
libavcodec/utils.c:1176: warning: assignment discards qualifiers from pointer target type
CC    libavcodec/v210dec.o
libavcodec/v210dec.c: In function ‘decode_frame’:
libavcodec/v210dec.c:79: warning: ‘val’ may be used uninitialized in this function
CC    libavcodec/v210enc.o
libavcodec/v210enc.c: In function ‘encode_frame’:
libavcodec/v210enc.c:78: warning: ‘val’ may be used uninitialized in this function
CC    libavcodec/v210x.o
CC    libavcodec/vb.o
CC    libavcodec/vc1.o
CC    libavcodec/vc1_parser.o
CC    libavcodec/vc1data.o
CC    libavcodec/vc1dec.o
libavcodec/vc1dec.c: In function ‘vc1_decode_p_mb’:
libavcodec/vc1dec.c:2319: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
CC    libavcodec/vc1dsp.o
CC    libavcodec/vcr1.o
CC    libavcodec/vmdav.o
CC    libavcodec/vmnc.o
CC    libavcodec/vorbis.o
CC    libavcodec/vorbis_data.o
CC    libavcodec/vorbis_dec.o
CC    libavcodec/vorbis_enc.o
CC    libavcodec/vp3.o
libavcodec/vp3.c: In function ‘vp3_decode_frame’:
libavcodec/vp3.c:619: warning: ‘motion_x[3]’ may be used uninitialized in this function
libavcodec/vp3.c:619: note: ‘motion_x[3]’ was declared here
libavcodec/vp3.c:619: warning: ‘motion_x[2]’ may be used uninitialized in this function
libavcodec/vp3.c:619: note: ‘motion_x[2]’ was declared here
libavcodec/vp3.c:619: warning: ‘motion_x[1]’ may be used uninitialized in this function
libavcodec/vp3.c:619: note: ‘motion_x[1]’ was declared here
libavcodec/vp3.c:620: warning: ‘motion_y[3]’ may be used uninitialized in this function
libavcodec/vp3.c:620: note: ‘motion_y[3]’ was declared here
libavcodec/vp3.c:620: warning: ‘motion_y[2]’ may be used uninitialized in this function
libavcodec/vp3.c:620: note: ‘motion_y[2]’ was declared here
libavcodec/vp3.c:620: warning: ‘motion_y[1]’ may be used uninitialized in this function
libavcodec/vp3.c:620: note: ‘motion_y[1]’ was declared here
CC    libavcodec/vp3_parser.o
CC    libavcodec/vp3dsp.o
CC    libavcodec/vp5.o
CC    libavcodec/vp56.o
CC    libavcodec/vp56data.o
CC    libavcodec/vp6.o
CC    libavcodec/vp6dsp.o
CC    libavcodec/vqavideo.o
CC    libavcodec/wavpack.o
CC    libavcodec/wma.o
CC    libavcodec/wmadec.o
CC    libavcodec/wmaenc.o
CC    libavcodec/wmaprodec.o
libavcodec/wmaprodec.c: In function ‘decode_frame’:
libavcodec/wmaprodec.c:815: warning: dereferencing pointer ‘({anonymous})’ does break strict-aliasing rules
libavcodec/wmaprodec.c:815: note: initialized from here
CC    libavcodec/wmavoice.o
libavcodec/wmavoice.c: In function ‘synth_block_fcb_acb’:
libavcodec/wmavoice.c:925: warning: passing argument 1 of ‘av_memcpy_backptr’ from incompatible pointer type
./libavutil/lzo.h:64: note: expected ‘uint8_t *’ but argument is of type ‘float *’
libavcodec/wmavoice.c: In function ‘wmavoice_decode_packet’:
libavcodec/wmavoice.c:1468: warning: format ‘%lu’ expects type ‘long unsigned int’, but argument 5 has type ‘unsigned int’
CC    libavcodec/wmv2.o
CC    libavcodec/wmv2dec.o
CC    libavcodec/wmv2enc.o
CC    libavcodec/wnv1.o
CC    libavcodec/ws-snd1.o
CC    libavcodec/x86/cavsdsp_mmx.o
CC    libavcodec/x86/cpuid.o
CC    libavcodec/x86/dnxhd_mmx.o
CC    libavcodec/x86/dsputil_mmx.o
YASM    libavcodec/x86/dsputil_yasm.o
CC    libavcodec/x86/dsputilenc_mmx.o
CC    libavcodec/x86/fdct_mmx.o
CC    libavcodec/x86/fft.o
CC    libavcodec/x86/fft_3dn.o
CC    libavcodec/x86/fft_3dn2.o
YASM    libavcodec/x86/fft_mmx.o
CC    libavcodec/x86/fft_sse.o
YASM    libavcodec/x86/h264_deblock_sse2.o
YASM    libavcodec/x86/h264_idct_sse2.o
CC    libavcodec/x86/idct_mmx.o
In file included from libavcodec/x86/idct_mmx.c:27:
libavcodec/x86/mmx.h:24:2: warning: #warning Everything in this header is deprecated, use plain __asm__()! New code using this header will be rejected.
CC    libavcodec/x86/idct_mmx_xvid.o
CC    libavcodec/x86/idct_sse2_xvid.o
CC    libavcodec/x86/lpc_mmx.o
CC    libavcodec/x86/mlpdsp.o
CC    libavcodec/x86/motion_est_mmx.o
CC    libavcodec/x86/mpegvideo_mmx.o
CC    libavcodec/x86/simple_idct_mmx.o
CC    libavcodec/x86/snowdsp_mmx.o
CC    libavcodec/x86/vc1dsp_mmx.o
CC    libavcodec/x86/vp3dsp_mmx.o
CC    libavcodec/x86/vp3dsp_sse2.o
CC    libavcodec/x86/vp6dsp_mmx.o
CC    libavcodec/x86/vp6dsp_sse2.o
CC    libavcodec/xan.o
libavcodec/xan.c: In function ‘xan_decode_frame’:
libavcodec/xan.c:364: warning: ‘AVPaletteControl’ is deprecated
CC    libavcodec/xiph.o
CC    libavcodec/xl.o
CC    libavcodec/xsubdec.o
CC    libavcodec/xsubenc.o
CC    libavcodec/zmbv.o
libavcodec/zmbv.c: In function ‘decode_frame’:
libavcodec/zmbv.c:496: warning: assignment discards qualifiers from pointer target type
CC    libavcodec/zmbvenc.o
AR    libavcodec/libavcodec.a
INSTALL    libavcodec/libavcodec.a
CC    libpostproc/postprocess.o
AR    libpostproc/libpostproc.a
INSTALL    libpostproc/libpostproc.a
CC    libswscale/options.o
CC    libswscale/rgb2rgb.o
CC    libswscale/swscale.o
In file included from libswscale/swscale.c:1225:
libswscale/swscale_template.c: In function ‘yuv2yuv1_MMX2’:
libswscale/swscale_template.c:957: warning: initialization from incompatible pointer type
libswscale/swscale_template.c:957: warning: initialization from incompatible pointer type
libswscale/swscale_template.c:957: warning: initialization from incompatible pointer type
libswscale/swscale_template.c:957: warning: initialization from incompatible pointer type
libswscale/swscale_template.c: In function ‘yuv2packed2_MMX2’:
libswscale/swscale_template.c:1238: warning: dereferencing type-punned pointer will break strict-aliasing rules
libswscale/swscale_template.c:1239: warning: dereferencing type-punned pointer will break strict-aliasing rules
libswscale/swscale_template.c: In function ‘hyscale_fast_MMX2’:
libswscale/swscale_template.c:2263: warning: initialization from incompatible pointer type
libswscale/swscale_template.c: In function ‘hcscale_fast_MMX2’:
libswscale/swscale_template.c:2412: warning: initialization from incompatible pointer type
libswscale/swscale_template.c: In function ‘swScale_MMX2’:
libswscale/swscale_template.c:2767: warning: cast from pointer to integer of different size
libswscale/swscale_template.c:2773: warning: cast from pointer to integer of different size
libswscale/swscale_template.c:2780: warning: cast from pointer to integer of different size
libswscale/swscale_template.c: In function ‘sws_init_swScale_MMX2’:
libswscale/swscale_template.c:2968: warning: assignment from incompatible pointer type
libswscale/swscale_template.c:2983: warning: assignment from incompatible pointer type
libswscale/swscale_template.c:3028: warning: assignment from incompatible pointer type
CC    libswscale/utils.o
libswscale/utils.c: In function ‘sws_getContext’:
libswscale/utils.c:978: warning: passing argument 5 of ‘initMMX2HScaler’ from incompatible pointer type
libswscale/utils.c:512: note: expected ‘int32_t *’ but argument is of type ‘int16_t *’
libswscale/utils.c:979: warning: passing argument 5 of ‘initMMX2HScaler’ from incompatible pointer type
libswscale/utils.c:512: note: expected ‘int32_t *’ but argument is of type ‘int16_t *’
CC    libswscale/x86/yuv2rgb_mmx.o
In file included from libswscale/x86/yuv2rgb_mmx.c:52:
libswscale/x86/yuv2rgb_template.c: In function ‘yuva420_rgb32_MMX’:
libswscale/x86/yuv2rgb_template.c:528: warning: no return statement in function returning non-void
libswscale/x86/yuv2rgb_template.c: In function ‘yuva420_bgr32_MMX’:
libswscale/x86/yuv2rgb_template.c:564: warning: no return statement in function returning non-void
In file included from libswscale/x86/yuv2rgb_mmx.c:59:
libswscale/x86/yuv2rgb_template.c: In function ‘yuva420_rgb32_MMX2’:
libswscale/x86/yuv2rgb_template.c:528: warning: no return statement in function returning non-void
libswscale/x86/yuv2rgb_template.c: In function ‘yuva420_bgr32_MMX2’:
libswscale/x86/yuv2rgb_template.c:564: warning: no return statement in function returning non-void
CC    libswscale/yuv2rgb.o
libswscale/yuv2rgb.c: In function ‘ff_yuv2rgb_c_init_tables’:
libswscale/yuv2rgb.c:754: warning: passing argument 4 of ‘fill_table’ from incompatible pointer type
libswscale/yuv2rgb.c:598: note: expected ‘uint8_t *’ but argument is of type ‘uint16_t *’
libswscale/yuv2rgb.c:755: warning: passing argument 4 of ‘fill_table’ from incompatible pointer type
libswscale/yuv2rgb.c:598: note: expected ‘uint8_t *’ but argument is of type ‘uint16_t *’
libswscale/yuv2rgb.c:756: warning: passing argument 4 of ‘fill_table’ from incompatible pointer type
libswscale/yuv2rgb.c:598: note: expected ‘uint8_t *’ but argument is of type ‘uint16_t *’
libswscale/yuv2rgb.c:777: warning: passing argument 4 of ‘fill_table’ from incompatible pointer type
libswscale/yuv2rgb.c:598: note: expected ‘uint8_t *’ but argument is of type ‘uint16_t *’
libswscale/yuv2rgb.c:778: warning: passing argument 4 of ‘fill_table’ from incompatible pointer type
libswscale/yuv2rgb.c:598: note: expected ‘uint8_t *’ but argument is of type ‘uint16_t *’
libswscale/yuv2rgb.c:779: warning: passing argument 4 of ‘fill_table’ from incompatible pointer type
libswscale/yuv2rgb.c:598: note: expected ‘uint8_t *’ but argument is of type ‘uint16_t *’
libswscale/yuv2rgb.c:814: warning: passing argument 4 of ‘fill_table’ from incompatible pointer type
libswscale/yuv2rgb.c:598: note: expected ‘uint8_t *’ but argument is of type ‘uint32_t *’
libswscale/yuv2rgb.c:815: warning: passing argument 4 of ‘fill_table’ from incompatible pointer type
libswscale/yuv2rgb.c:598: note: expected ‘uint8_t *’ but argument is of type ‘uint32_t *’
libswscale/yuv2rgb.c:816: warning: passing argument 4 of ‘fill_table’ from incompatible pointer type
libswscale/yuv2rgb.c:598: note: expected ‘uint8_t *’ but argument is of type ‘uint32_t *’
libswscale/yuv2rgb.c:649: warning: ‘abase’ may be used uninitialized in this function
AR    libswscale/libswscale.a
INSTALL    libswscale/libswscale.a
CC    libavutil/adler32.o
CC    libavutil/aes.o
libavutil/aes.c: In function ‘subshift’:
libavutil/aes.c:56: warning: initialization from incompatible pointer type
libavutil/aes.c:57: warning: initialization from incompatible pointer type
libavutil/aes.c: In function ‘crypt’:
libavutil/aes.c:84: warning: passing argument 2 of ‘mix’ from incompatible pointer type
libavutil/aes.c:73: note: expected ‘uint32_t (*)[256]’ but argument is of type ‘const uint32_t *’
libavutil/aes.c:85: warning: passing argument 1 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:85: warning: passing argument 2 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:85: warning: passing argument 3 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:87: warning: passing argument 1 of ‘subshift’ from incompatible pointer type
libavutil/aes.c:55: note: expected ‘uint8_t (*)[16]’ but argument is of type ‘uint8_t *’
libavutil/aes.c: In function ‘av_aes_crypt’:
libavutil/aes.c:92: warning: passing argument 1 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:92: warning: passing argument 2 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘const uint8_t *’
libavutil/aes.c:92: warning: passing argument 3 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:94: warning: passing argument 4 of ‘crypt’ from incompatible pointer type
libavutil/aes.c:80: note: expected ‘const uint32_t *’ but argument is of type ‘uint32_t (*)[256]’
libavutil/aes.c:96: warning: passing argument 1 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:96: warning: passing argument 2 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:96: warning: passing argument 3 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘uint8_t *’
libavutil/aes.c:99: warning: passing argument 1 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘uint64_t *’ but argument is of type ‘uint8_t *’
libavutil/aes.c:99: warning: passing argument 2 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:99: warning: passing argument 3 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:101: warning: passing argument 1 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:101: warning: passing argument 2 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:101: warning: passing argument 3 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘uint8_t *’
libavutil/aes.c:102: warning: passing argument 4 of ‘crypt’ from incompatible pointer type
libavutil/aes.c:80: note: expected ‘const uint32_t *’ but argument is of type ‘uint32_t (*)[256]’
libavutil/aes.c:103: warning: passing argument 1 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘uint64_t *’ but argument is of type ‘uint8_t *’
libavutil/aes.c:103: warning: passing argument 2 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c:103: warning: passing argument 3 of ‘addkey’ from incompatible pointer type
libavutil/aes.c:50: note: expected ‘const uint64_t *’ but argument is of type ‘uint8_t (*)[4]’
libavutil/aes.c: In function ‘av_aes_init’:
libavutil/aes.c:149: warning: passing argument 1 of ‘init_multbl2’ from incompatible pointer type
libavutil/aes.c:111: note: expected ‘uint8_t *’ but argument is of type ‘uint32_t *’
libavutil/aes.c:150: warning: passing argument 1 of ‘init_multbl2’ from incompatible pointer type
libavutil/aes.c:111: note: expected ‘uint8_t *’ but argument is of type ‘uint32_t *’
libavutil/aes.c:180: warning: passing argument 1 of ‘subshift’ from incompatible pointer type
libavutil/aes.c:55: note: expected ‘uint8_t (*)[16]’ but argument is of type ‘uint8_t *’
libavutil/aes.c:181: warning: passing argument 1 of ‘mix’ from incompatible pointer type
libavutil/aes.c:73: note: expected ‘uint8_t (*)[4][4]’ but argument is of type ‘uint8_t (*)[16]’
libavutil/aes.c:133: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
libavutil/aes.c:187: warning: array subscript is above array bounds
CC    libavutil/avstring.o
libavutil/avstring.c: In function ‘av_stristr’:
libavutil/avstring.c:54: warning: return discards qualifiers from pointer target type
libavutil/avstring.c:58: warning: return discards qualifiers from pointer target type
CC    libavutil/base64.o
CC    libavutil/crc.o
CC    libavutil/des.o
CC    libavutil/fifo.o
CC    libavutil/intfloat_readwrite.o
CC    libavutil/lfg.o
CC    libavutil/lls.o
CC    libavutil/log.o
CC    libavutil/lzo.o
CC    libavutil/mathematics.o
libavutil/mathematics.c: In function ‘av_rescale_rnd’:
libavutil/mathematics.c:81: warning: comparison of unsigned expression >= 0 is always true
CC    libavutil/md5.o
CC    libavutil/mem.o
CC    libavutil/pixdesc.o
CC    libavutil/random_seed.o
CC    libavutil/rational.o
CC    libavutil/rc4.o
CC    libavutil/sha.o
CC    libavutil/tree.o
CC    libavutil/utils.o
AR    libavutil/libavutil.a
INSTALL    libavutil/libavutil.a
INSTALL    libavdevice/avdevice.h
INSTALL    libavdevice/libavdevice.pc
INSTALL    libavformat/avformat.h
INSTALL    libavformat/avio.h
INSTALL    libavformat/libavformat.pc
INSTALL    libavcodec/avcodec.h
INSTALL    libavcodec/avfft.h
INSTALL    libavcodec/dxva2.h
INSTALL    libavcodec/opt.h
INSTALL    libavcodec/vaapi.h
INSTALL    libavcodec/vdpau.h
INSTALL    libavcodec/xvmc.h
INSTALL    libavcodec/libavcodec.pc
INSTALL    libpostproc/postprocess.h
INSTALL    libpostproc/libpostproc.pc
INSTALL    libswscale/swscale.h
INSTALL    libswscale/libswscale.pc
INSTALL    libavutil/adler32.h
INSTALL    libavutil/attributes.h
INSTALL    libavutil/avstring.h
INSTALL    libavutil/avutil.h
INSTALL    libavutil/base64.h
INSTALL    libavutil/common.h
INSTALL    libavutil/crc.h
INSTALL    libavutil/error.h
INSTALL    libavutil/fifo.h
INSTALL    libavutil/intfloat_readwrite.h
INSTALL    libavutil/log.h
INSTALL    libavutil/lzo.h
INSTALL    libavutil/mathematics.h
INSTALL    libavutil/md5.h
INSTALL    libavutil/mem.h
INSTALL    libavutil/pixdesc.h
INSTALL    libavutil/pixfmt.h
INSTALL    libavutil/rational.h
INSTALL    libavutil/sha1.h
INSTALL    libavutil/avconfig.h
INSTALL    libavutil/libavutil.pc
CC    ffmpeg.o
ffmpeg.c: In function ‘do_video_out’:
ffmpeg.c:1029: warning: passing argument 2 of ‘sws_scale’ from incompatible pointer type
libswscale/swscale.h:195: note: expected ‘const uint8_t * const*’ but argument is of type ‘uint8_t **’
ffmpeg.c: In function ‘output_packet’:
ffmpeg.c:819: warning: dereferencing pointer ‘picture2’ does break strict-aliasing rules
ffmpeg.c:1419: note: initialized from here
CC    cmdutils.o
LD    ffmpeg_g
/home/me/ffmpeg/libavcodec/libavcodec.a(libx264.o): In function `X264_init':
/home/me/ffmpeg/libavcodec/libx264.c:286: undefined reference to `x264_encoder_open_88'
collect2: ld returned 1 exit status
make: *** [ffmpeg_g] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.


and here is the  ./configure
> ./configure --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libgsm --enable-postproc --enable-libxvid --enable-libfaac --enable-pthreads --enable-libvorbis --enable-libfaad --enable-gpl --enable-nonfree --enable-x11grab --enable-swscale --enable-version3 --enable-pthreads

Help please

---

### Post by Yellow Pasque on 2010-03-18
Your version of libx264-dev isn't current enough. You can grab the latest .debs of libx264-dev and libx264-88 from the unstable/sid branch at: [http://www.debian-multimedia.org/dists/unstable/main/binary-i386/](http://www.debian-multimedia.org/dists/unstable/main/binary-i386/) (32-bit) or 
[http://www.debian-multimedia.org/dists/unstable/main/binary-amd64](http://www.debian-multimedia.org/dists/unstable/main/binary-amd64) (64-bit)

---

### Post by mc4man on 2010-03-18
I'm thinking you may of built a new. current x264 (core 88),(that damn simile is an eight), most likely to /usr/local (if so probably a static build which is fine

If so, then the error indicates you didn't remove libx264-dev that is installed in /usr and it is a lesser core version

You can have multiple versions of libx264-XX installed at the same time *(though only one install per core version. (-XX)*

So while generally there is no need to remove libx264-XX prior to building a new, current x264 and ffmpeg, you can only have 1 install of x264 headers

(provided by either a static x264 build or a packaged libx264-dev

If you did just, or very recently build x264, then remove the libx264-dev package
```
sudo apt-get remove libx264-dev
```

Then clean your ffmpeg source (make distclean), configure it as before, make and it should build fine

The other direction (if you did just build x264), is to remove your recent build and use the debian package set as previously described.

*using a libx264-dev (which then creates a depend on libx264-XX) is* not* my preferred method




I prefer to keep x264 and ffmpeg as static builds so when I build sources off of them they are statically linked and I don't need to maintain dependencies - in other words I can freely remove, upgrade x264 and ffmpeg

---

### Post by hazelnut on 2010-03-18
WARNING

I did this last week and spent the next few days fixing a broken video system.  I compiled the latest X264 then the latest ffmpeg.  Lo and behold, mplayer is now borken!  Finally managed to recompile mplayer to fix that, but found vlc to be broken!  

I finally gave up and uninstalled all video crap.  Then installed x264 sources from the repositories--built that.  Then installed ffmpeg sources from the repositories--built that.  Then installed mplayer binary from repositories, and finally installed vlc binary from the repositories.  Whew! #-o

I'm not touching it again until the ffmpeg developers stop breaking the shared libraries.

---

### Post by mc4man on 2010-03-18
> I'm not touching it again until the ffmpeg developers stop breaking the shared libraries. 
If you are going to build ffmpeg **as shared** then you should be aware beforehand of the potential issues and possible breakage of repo apps that depend on those libs, balance that against the very limited gains that new shared libs provide and adjust accordingly.

 
Has nothing to do with ffmpeg or it's developers...

---

