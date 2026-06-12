---
title: "mplayer compilation error"
date: 2012-03-18
forum: Multimedia Software
---

### Post by rzippert on 2012-03-18
Hello everyone. Hope someone can help me out.

Recently I recompiled x264, ffmpeg, mplayer/mencoder and tried to make these programs work together smoothly. Was having errors but following some tutorials I found around here I managed to make'em all install.

Problem is that later I noticed that mencoder is unable to convert anything with libav. It gives me an error as if it can't initialize the codec. That was ok, so I tried to encode something with ffmpeg to a codec covered by libav, such as mpeg4 (which is the one I need actually), and it worked flawlessly. Also mencoder is able to convert anything with x264 instead of libav, for example.

I came to the conclusion that it's all fine with ffmpeg then, and that I should recompile mplayer to make it work again. Right now I got a new checkout from svn to a clean folder, have let it download ffmpeg itself from git, ./configured, but when I use make (not trying any parameter) it goes all the way through libav but exits with an error I can't understand.

The end of the messages (which I believe are the relevant ones):
```
blablabla...
libavutil/opt.c:601:5: warning: 'av_opt_set_defaults2' is deprecated (declared at libavutil/opt.h:370)
CC      libavutil/parseutils.o
CC      libavutil/pixdesc.o
CC      libavutil/random_seed.o
CC      libavutil/rational.o
CC      libavutil/rc4.o
CC      libavutil/samplefmt.o
CC      libavutil/sha.o
CC      libavutil/timecode.o
CC      libavutil/tree.o
CC      libavutil/utils.o
CC      libavutil/x86/cpu.o
AR      libavutil/libavutil.a
make[1]: Leaving directory `/mnt/sdb3/Builds/mplayer/ffmpeg'
cc -o mplayer command.o m_property.o mixer.o mp_fifo.o mplayer.o parser-mpcmd.o pnm_loader.o input/input.o libao2/ao_mpegpes.o libao2/ao_null.o libao2/ao_pcm.o libao2/audio_out.o libvo/aspect.o libvo/geometry.o libvo/video_out.o libvo/vo_mpegpes.o libvo/vo_null.o sub/spuenc.o libvo/vo_aa.o libao2/ao_alsa.o input/appleir.o libvo/vo_caca.o libvo/vo_dga.o libvo/vo_directfb2.o libvo/vo_dfbmga.o libao2/ao_esd.o libvo/vo_fbdev.o libvo/vo_fbdev2.o libvo/vo_png.o libvo/vo_gif89a.o libvo/gl_common.o libvo/vo_gl.o libvo/vo_gl2.o libvo/csputils.o libvo/sdl_common.o libvo/x11_common.o libvo/vo_matrixview.o libvo/matrixview.o libao2/ao_jack.o libvo/vo_jpeg.o libvo/vo_md5sum.o libao2/ao_nas.o udp_sync.o libao2/ao_openal.o libao2/ao_oss.o libvo/vo_pnm.o libao2/ao_pulse.o libao2/ao_sdl.o libvo/vo_sdl.o libvo/vo_svga.o libvo/vo_tga.o libvo/vo_v4l2.o libao2/ao_v4l2.o libvo/vo_vdpau.o libvo/vo_cvidix.o libvo/vosub_vidix.o vidix/vidix.o vidix/drivers.o vidix/dha.o vidix/mtrr.o vidix/pci.o vidix/pci_names.o vidix/pci_dev_ids.o vidix/cyberblade_vid.o vidix/mach64_vid.o vidix/mga_vid.o vidix/mga_crtc2_vid.o vidix/nvidia_vid.o vidix/pm2_vid.o vidix/pm3_vid.o vidix/radeon_vid.o vidix/rage128_vid.o vidix/s3_vid.o vidix/sis_vid.o vidix/sis_bridge.o vidix/unichrome_vid.o libvo/vo_x11.o libvo/vo_xover.o libvo/vo_xv.o libvo/vo_xvidix.o libvo/vo_yuv4mpeg.o asxparser.o bstr.o codec-cfg.o cpudetect.o edl.o fmt-conversion.o m_config.o m_option.o m_struct.o mp_msg.o mp_strings.o mpcommon.o parser-cfg.o path.o playtree.o playtreeparser.o subopt-helper.o libaf/af.o libaf/af_center.o libaf/af_channels.o libaf/af_comp.o libaf/af_delay.o libaf/af_dummy.o libaf/af_equalizer.o libaf/af_extrastereo.o libaf/af_format.o libaf/af_gate.o libaf/af_hrtf.o libaf/af_karaoke.o libaf/af_pan.o libaf/af_resample.o libaf/af_scaletempo.o libaf/af_sinesuppress.o libaf/af_stats.o libaf/af_sub.o libaf/af_surround.o libaf/af_sweep.o libaf/af_tools.o libaf/af_volnorm.o libaf/af_volume.o libaf/filter.o libaf/format.o libaf/reorder_ch.o libaf/window.o libmpcodecs/ad.o libmpcodecs/ad_alaw.o libmpcodecs/ad_dk3adpcm.o libmpcodecs/ad_dvdpcm.o libmpcodecs/ad_hwac3.o libmpcodecs/ad_hwmpa.o libmpcodecs/ad_imaadpcm.o libmpcodecs/ad_msadpcm.o libmpcodecs/ad_pcm.o libmpcodecs/dec_audio.o libmpcodecs/dec_teletext.o libmpcodecs/dec_video.o libmpcodecs/img_format.o libmpcodecs/mp_image.o libmpcodecs/pullup.o libmpcodecs/vd.o libmpcodecs/vd_hmblck.o libmpcodecs/vd_lzo.o libmpcodecs/vd_mpegpes.o libmpcodecs/vd_mtga.o libmpcodecs/vd_null.o libmpcodecs/vd_raw.o libmpcodecs/vd_sgi.o libmpcodecs/vf.o libmpcodecs/vf_1bpp.o libmpcodecs/vf_2xsai.o libmpcodecs/vf_blackframe.o libmpcodecs/vf_boxblur.o libmpcodecs/vf_crop.o libmpcodecs/vf_cropdetect.o libmpcodecs/vf_decimate.o libmpcodecs/vf_delogo.o libmpcodecs/vf_denoise3d.o libmpcodecs/vf_detc.o libmpcodecs/vf_dint.o libmpcodecs/vf_divtc.o libmpcodecs/vf_down3dright.o libmpcodecs/vf_dsize.o libmpcodecs/vf_dvbscale.o libmpcodecs/vf_eq.o libmpcodecs/vf_eq2.o libmpcodecs/vf_expand.o libmpcodecs/vf_field.o libmpcodecs/vf_fil.o libmpcodecs/vf_filmdint.o libmpcodecs/vf_fixpts.o libmpcodecs/vf_flip.o libmpcodecs/vf_format.o libmpcodecs/vf_framestep.o libmpcodecs/vf_gradfun.o libmpcodecs/vf_halfpack.o libmpcodecs/vf_harddup.o libmpcodecs/vf_hqdn3d.o libmpcodecs/vf_hue.o libmpcodecs/vf_il.o libmpcodecs/vf_ilpack.o libmpcodecs/vf_ivtc.o libmpcodecs/vf_kerndeint.o libmpcodecs/vf_mirror.o libmpcodecs/vf_noformat.o libmpcodecs/vf_noise.o libmpcodecs/vf_ow.o libmpcodecs/vf_palette.o libmpcodecs/vf_perspective.o libmpcodecs/vf_phase.o libmpcodecs/vf_pp7.o libmpcodecs/vf_pullup.o libmpcodecs/vf_rectangle.o libmpcodecs/vf_remove_logo.o libmpcodecs/vf_rgbtest.o libmpcodecs/vf_rotate.o libmpcodecs/vf_sab.o libmpcodecs/vf_scale.o libmpcodecs/vf_smartblur.o libmpcodecs/vf_softpulldown.o libmpcodecs/vf_stereo3d.o libmpcodecs/vf_softskip.o libmpcodecs/vf_swapuv.o libmpcodecs/vf_telecine.o libmpcodecs/vf_test.o libmpcodecs/vf_tfields.o libmpcodecs/vf_tile.o libmpcodecs/vf_tinterlace.o libmpcodecs/vf_unsharp.o libmpcodecs/vf_vo.o libmpcodecs/vf_yadif.o libmpcodecs/vf_yuvcsp.o libmpcodecs/vf_yvu9.o libmpdemux/aac_hdr.o libmpdemux/asfheader.o libmpdemux/aviheader.o libmpdemux/aviprint.o libmpdemux/demuxer.o libmpdemux/demux_aac.o libmpdemux/demux_asf.o libmpdemux/demux_audio.o libmpdemux/demux_avi.o libmpdemux/demux_demuxers.o libmpdemux/demux_film.o libmpdemux/demux_fli.o libmpdemux/demux_lmlm4.o libmpdemux/demux_mf.o libmpdemux/demux_mkv.o libmpdemux/demux_mov.o libmpdemux/demux_mpg.o libmpdemux/demux_nsv.o libmpdemux/demux_pva.o libmpdemux/demux_rawaudio.o libmpdemux/demux_rawvideo.o libmpdemux/demux_realaud.o libmpdemux/demux_real.o libmpdemux/demux_roq.o libmpdemux/demux_smjpeg.o libmpdemux/demux_ts.o libmpdemux/demux_ty.o libmpdemux/demux_ty_osd.o libmpdemux/demux_viv.o libmpdemux/demux_vqf.o libmpdemux/demux_y4m.o libmpdemux/ebml.o libmpdemux/extension.o libmpdemux/mf.o libmpdemux/mp3_hdr.o libmpdemux/mp_taglists.o libmpdemux/mpeg_hdr.o libmpdemux/mpeg_packetizer.o libmpdemux/parse_es.o libmpdemux/parse_mp4.o libmpdemux/video.o libmpdemux/yuv4mpeg.o libmpdemux/yuv4mpeg_ratio.o osdep/getch2.o osdep/timer-linux.o stream/open.o stream/stream.o stream/stream_bd.o stream/stream_cue.o stream/stream_file.o stream/stream_mf.o stream/stream_null.o stream/url.o sub/eosd.o sub/find_sub.o sub/osd.o sub/spudec.o sub/sub.o sub/sub_cc.o sub/subreader.o sub/vobsub.o stream/ai_alsa.o stream/ai_oss.o sub/font_load.o stream/stream_cdda.o stream/cdinfo.o stream/stream_cddb.o stream/dvb_tune.o stream/stream_dvb.o stream/stream_dvdnav.o libdvdnav/dvdnav.o libdvdnav/highlight.o libdvdnav/navigation.o libdvdnav/read_cache.o libdvdnav/remap.o libdvdnav/searching.o libdvdnav/settings.o libdvdnav/vm/decoder.o libdvdnav/vm/vm.o libdvdnav/vm/vmcmd.o stream/stream_dvd.o stream/stream_dvd_common.o libdvdread4/bitreader.o libdvdread4/dvd_input.o libdvdread4/dvd_reader.o libdvdread4/dvd_udf.o libdvdread4/ifo_print.o libdvdread4/ifo_read.o libdvdread4/md5.o libdvdread4/nav_print.o libdvdread4/nav_read.o libmpcodecs/ad_faad.o libvo/aclib.o av_helpers.o av_opts.o libaf/af_lavcac3enc.o libaf/af_lavcresample.o libmpcodecs/ad_ffmpeg.o libmpcodecs/ad_spdif.o libmpcodecs/vd_ffmpeg.o libmpcodecs/vf_geq.o libmpcodecs/vf_lavc.o libmpcodecs/vf_lavcdeint.o libmpcodecs/vf_screenshot.o libmpdemux/demux_lavf.o stream/stream_ffmpeg.o sub/av_sub.o libmpcodecs/vf_fspp.o libmpcodecs/vf_mcdeint.o libmpcodecs/vf_qp.o libmpcodecs/vf_spp.o libmpcodecs/vf_uspp.o sub/font_load_ft.o stream/stream_ftp.o libmpdemux/demux_gif.o libmpcodecs/vf_bmovl.o libaf/af_export.o osdep/mmap_anon.o libmpcodecs/vd_ijpg.o libmpcodecs/vf_***.o sub/***_mp.o sub/subassconvert.o libass/***.o libass/***_bitmap.o libass/***_cache.o libass/***_drawing.o libass/***_font.o libass/***_fontconfig.o libass/***_library.o libass/***_parse.o libass/***_render.o libass/***_render_api.o libass/***_shaper.o libass/***_strtod.o libass/***_utils.o libdvdcss/css.o libdvdcss/device.o libdvdcss/error.o libdvdcss/ioctl.o libdvdcss/libdvdcss.o libmpcodecs/ad_libmad.o libmpcodecs/vd_libmpeg2.o libmpeg2/alloc.o libmpeg2/cpu_accel.o libmpeg2/cpu_state.o libmpeg2/decode.o libmpeg2/header.o libmpeg2/idct.o libmpeg2/motion_comp.o libmpeg2/slice.o libmpeg2/idct_mmx.o libmpeg2/motion_comp_mmx.o libmpcodecs/vd_theora.o libmpdemux/demux_rtp.o libmpdemux/demux_rtp_codec.o stream/stream_live555.o libmpcodecs/ad_mpg123.o libmpcodecs/ad_mp3lib.o mp3lib/sr1.o mp3lib/decode_mmx.o mp3lib/dct64_sse.o stream/stream_rtsp.o stream/freesdp/common.o stream/freesdp/errorlist.o stream/freesdp/parser.o stream/librtsp/rtsp.o stream/librtsp/rtsp_rtp.o stream/librtsp/rtsp_session.o stream/stream_netstream.o stream/asf_mmst_streaming.o stream/asf_streaming.o stream/cookies.o stream/http.o stream/network.o stream/pnm.o stream/rtp.o stream/udp.o stream/tcp.o stream/stream_rtp.o stream/stream_udp.o stream/realrtsp/asmrp.o stream/realrtsp/real.o stream/realrtsp/rmff.o stream/realrtsp/sdpplin.o stream/realrtsp/xbuffer.o libmpcodecs/vd_mpng.o libmpcodecs/vf_pp.o stream/stream_pvr.o libmpcodecs/ad_realaud.o libmpcodecs/vd_realvid.o stream/cache2.o tremor/bitwise.o tremor/block.o tremor/codebook.o tremor/floor0.o tremor/floor1.o tremor/framing.o tremor/info.o tremor/mapping0.o tremor/mdct.o tremor/registry.o tremor/res012.o tremor/sharedbook.o tremor/synthesis.o tremor/window.o stream/stream_tv.o stream/tv.o stream/frequencies.o stream/tvi_dummy.o stream/tvi_v4l2.o stream/audio_in.o sub/unrar_exec.o stream/stream_vcd.o libmpcodecs/ad_libvorbis.o libmpdemux/demux_ogg.o libmpcodecs/vd_xanim.o libmpcodecs/vd_xvid4.o osdep/shmem.o ffmpeg/libpostproc/libpostproc.a ffmpeg/libavfilter/libavfilter.a ffmpeg/libavformat/libavformat.a ffmpeg/libavcodec/libavcodec.a ffmpeg/libswscale/libswscale.a ffmpeg/libswresample/libswresample.a ffmpeg/libavutil/libavutil.a -Wl,-z,noexecstack /usr/lib/live/liveMedia/libliveMedia.a                  /usr/lib/live/UsageEnvironment/libUsageEnvironment.a                  /usr/lib/live/BasicUsageEnvironment/libBasicUsageEnvironment.a                  /usr/lib/live/groupsock/libgroupsock.a                  -lm  -ffast-math   -lncurses -lpng -lz -ljpeg -lungif -lasound -ldl -lpthread -lcdda_interface -lcdda_paranoia -L/usr/lib/x86_64-linux-gnu -lfreetype -lz -lfontconfig  -lfribidi -lenca -lz -lbz2 -lmad -ltheoradec -logg -lmpg123 -lfaad  -lstdc++  -lrtmp -lopencore-amrnb -lopencore-amrwb -lxvidcore -lpthread -ldl -rdynamic -L/usr/lib   -ldirectfb -lXext -lX11 -lpthread -lXss -lXv -lvdpau -lXinerama -lXxf86vm -lXxf86dga -laa -lcaca -lvga -lSDL -lGL -ldl -lesd -laudio -lXt -lpulse -ljack -lopenal -lfaac -lx264 -lpthread -lmp3lame
libmpdemux/demux_rtp.o: In function `demux_close_rtp':
demux_rtp.cpp:(.text+0xd6): undefined reference to `RTSPClient::teardownMediaSession(MediaSession&)'
libmpdemux/demux_rtp.o: In function `demux_open_rtp':
demux_rtp.cpp:(.text+0x77a): undefined reference to `RTSPClient::setupMediaSubsession(MediaSubsession&, unsigned int, unsigned int, unsigned int)'
demux_rtp.cpp:(.text+0x85b): undefined reference to `RTSPClient::playMediaSession(MediaSession&, double, double, float)'
demux_rtp.cpp:(.text+0xad9): undefined reference to `RTSPClient::createNew(UsageEnvironment&, int, char const*, unsigned short)'
demux_rtp.cpp:(.text+0xb20): undefined reference to `RTSPClient::describeWithPassword(char const*, char const*, char const*, unsigned int, int)'
demux_rtp.cpp:(.text+0xc0c): undefined reference to `RTSPClient::describeURL(char const*, Authenticator*, unsigned int, int)'
collect2: ld returned 1 exit status
make: ** [mplayer] Erro 1

```

In case u're wondering about the "[mplayer] Erro 1", My Ubuntu is in portuguese. I'm on Natty btw.

Can anyone give me a tip on what to do to get it to compile? Or where I can get more info about this error... I really appreciate your attention.

---

### Post by andrew.46 on 2012-03-18
There is a problem with some of the newer live555 libraries. Perhaps the easiest thing is to add:
```

--disable-live
```

to your MPlayer ./configure string or consider using an older live555 version:

```
wget http://live555sourcecontrol.googlecode.com/files/live.2011.12.23.tar.gz
```

---

### Post by rzippert on 2012-03-19
Used --disable-live and it worked...

Thank you very much... But I got curious now. Could you tell me how did you know it was about live555?

---

### Post by andrew.46 on 2012-03-19
In part because I follow MPlayer development fairly closely, including the MPlayer-users mailing list, and in part because I bumped into this error myself :). I run a long thread that deals with building MPlayer somewhere on these Forums as well.....

---

### Post by rzippert on 2012-03-19
Thank you =)

---

### Post by MishMich on 2012-10-04
Hi Andrew,

I followed that post you referred to, and it was very helpful, although I am trying to get smplayer to run on Debian Wheezy. Most seemed to work OK, apart from the long list of packages to install. Thanks.

I would respond there, but 4 years on, the thread is closed, and although I do use ubuntu, I have been working through this on debian in preparation to start a linux from scratch build.

I have edited this, as I couldn't get sound to work. However, I installed all the alsa & pulse packages I could find, and re-installed using the option to include gmplayer, and both the CLI & smplayer now have working audio.

The ./configure does throw up quite a few warnings about missing parameters, and this line persists on the CLI, even though audio now works:

> [AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory

Reading through various threads, the response to this is usually to purge all the pulse packages from the system, but that seems to involve removing gnome, basically, which is undesirable.

I just wondered what Andrew's take on this is. And to say thanks for a great walkthrough.

---

