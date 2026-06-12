---
title: "totem-xine, miro: no sound, but sound works fine in xine-ui"
date: 2008-05-05
forum: Multimedia Software
---

### Post by misha1983 on 2008-05-05
Hi,

I've got xine set up to use the ALSA driver for output. This was done through xine-ui, and I can now play back videos and get sound.

I've got two other apps that use xine: miro and totem-xine. Playing videos through them works, but without sound.

Why would this be so? Aren't miro and totem-xine just using the same underlying engine as xine-ui to play the videos? What am I missing here?

Cheers,
Misha

PS. Sound wasn't working in xine-ui either before I changed the output to ALSA. Perhaps there are other configuration files that I need to edit, aside from ~/.xine/config (xine-ui looks after that one)?

---

### Post by misha1983 on 2008-05-10
Here's debug output for totem-xine when trying to play a movie:

```

load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_fli.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_vorbis.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_dxr3_video.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_pvr.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_nsf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_pva.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_caca.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_ao_out_esd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_mad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_rtsp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_gnome_vfs.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_spucmml.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_dvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_spucc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_faad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_xvmc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_xdirectfb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_xdirectfb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_dxr3_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_xxmc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_yuv_frames.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_directfb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_dvaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_yuv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_mng.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_mpeg_elem.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_http.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_gsm610.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_smb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_opengl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_ao_out_pulseaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_ao_out_alsa.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_flac.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_speex.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_switch.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_autocrop.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_tvtime.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_audiochannel.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_mosaico.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_goom.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_xcbxv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_avi.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_lpcm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_stdin_fifo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_ao_out_oss.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_dvd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_rgb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_mpeg_ts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_mms.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_vcdo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_net.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_cdda.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_mpeg_pes.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_xvdr.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_gdk_pixbuf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_aa.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_pnm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_wavpack.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_wavpack.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_yuv4mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_asf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_matroska.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_mpc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_theora.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_rtp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_dxr3.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_flv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_nsv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_rawdv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_slave.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_a52.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_ao_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_spudvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_syncfb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_mpeg_block.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_sdl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_iff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_xcbshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_bitplane.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_ao_out_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_dmx_mpeg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_decode_dts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_vo_out_fb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.20/xineplug_inp_vcd.so found
init class succeeded
params.c:OpenConfFile() - Unable to open configuration file "/home/misha/.smb/smb.conf":
	No such file or directory
params.c:OpenConfFile() - Unable to open configuration file "/home/misha/.smb/smb.conf.append":
	No such file or directory
Using netbios name POSEIDON.
Using workgroup MSHOME.
gnome_vfs init_input_class
video_out_xv: using Xv port 93 from adaptor NV10 Video Overlay for hardware colour space conversion and scaling.
video_out_xv: double buffering mode = 1
video_out_xv: port attribute XV_COLORKEY (6) value is 66051
video_out_xv: port attribute XV_AUTOPAINT_COLORKEY (7) value is 1
video_out_xv: port attribute XV_BRIGHTNESS (5) value is -2
video_out_xv: port attribute XV_CONTRAST (4) value is 4083
video_out_xv: port attribute XV_SATURATION (3) value is 4083
video_out_xv: ignoring broken XV_HUE settings on NVidia cards
video_out_xv: this adaptor supports the yuy2 format.
video_out_xv: this adaptor supports the yv12 format.
x11osd: unscaled overlay created (Colorkey mode).
video_out: thread created
audio_pulse_out: host (null) sink (null)
audio_out: thread created
xine_stream_new
load_plugins: no post plugin named GOOM: what a GOOM! found
video_out_xv: VO_PROP_INTERLACED(0)
libsputext: spu_src_encoding = utf-8
video_out_xv: VO_PROP_ZOOM_X = 100
video_out_xv: VO_PROP_ZOOM_Y = 100
xine: found input plugin  : file input plugin
load_plugins: probing demux 'anx'
load_plugins: probing demux 'image'
load_plugins: probing demux 'ogg'
load_plugins: probing demux 'pva'
load_plugins: probing demux 'aud'
load_plugins: probing demux 'aiff'
load_plugins: probing demux 'flac'
load_plugins: probing demux 'nsf'
load_plugins: probing demux 'realaudio'
load_plugins: probing demux 'snd'
load_plugins: probing demux 'tta'
load_plugins: probing demux 'voc'
load_plugins: probing demux 'vox'
load_plugins: probing demux 'mod'
TEST mod decode
load_plugins: probing demux 'quicktime'
load_plugins: probing demux 'wve'
load_plugins: probing demux 'idcin'
load_plugins: probing demux 'ipmovie'
load_plugins: probing demux 'vqa'
load_plugins: probing demux 'wc3movie'
load_plugins: probing demux 'roq'
load_plugins: probing demux 'str'
load_plugins: probing demux 'film'
load_plugins: probing demux 'smjpeg'
load_plugins: probing demux 'fourxm'
load_plugins: probing demux 'vmd'
load_plugins: probing demux 'mng'
load_plugins: probing demux 'avi'
failed to read 8 bytes at pos 1466845184
demux_avi: 157757 frames
xine: found demuxer plugin: AVI/RIFF demux plugin
demux_avi: audio format[0] = 0x2000
demux_avi: audio type AC3 (wFormatTag 0x2000)
video discontinuity #1, type is 0, disc_off 0
waiting for audio discontinuity #1
audio discontinuity #1, type is 0, disc_off 0
waiting for in_discontinuity update #1
vpts adjusted with prebuffer to 163552
demux_avi: video codec is 'XviD'
load_plugins: plugin ffmpegvideo will be used for video streamtype 1d.
load_plugins: plugin a/52 will be used for audio streamtype 00.
ffmpeg_video_dec: direct rendering enabled
audio_pulse_out: ao_open bits=16 rate=48000, mode=128
output sample rate 48000
ao_close
xine_play
ao_flush (loop running: 1)
start pos is 0, start time is 0
video_pts = 0
video discontinuity #2, type is 3, disc_off 0
waiting for audio discontinuity #2
audio discontinuity #2, type is 3, disc_off 0
waiting for in_discontinuity update #2
vpts adjusted with prebuffer to 172670
video discontinuity #3, type is 3, disc_off 0
waiting for audio discontinuity #3
audio discontinuity #3, type is 3, disc_off 0
waiting for in_discontinuity update #3
vpts adjusted with prebuffer to 172680
audio jump, diff=-960
video jump
play_internal ...done
xine_play
ao_flush (loop running: 1)
start pos is 0, start time is 10243
video_pts = 0
audio discontinuity #4, type is 3, disc_off 0
waiting for in_discontinuity update #4
video discontinuity #4, type is 3, disc_off 0
vpts adjusted with prebuffer to 382770
audio discontinuity #5, type is 3, disc_off 0
waiting for in_discontinuity update #5
video discontinuity #5, type is 3, disc_off 0
vpts adjusted with prebuffer to 382781
audio jump, diff=-960
video jump
play_internal ...done
xine_play
ao_flush (loop running: 1)
start pos is 0, start time is 573661
video_pts = 51321600
audio discontinuity #6, type is 3, disc_off 51321600
waiting for in_discontinuity update #6
video discontinuity #6, type is 3, disc_off 51321600
vpts adjusted with prebuffer to 395179
video discontinuity #7, type is 3, disc_off 51319799
waiting for audio discontinuity #7
audio discontinuity #7, type is 3, disc_off 51319799
waiting for in_discontinuity update #7
vpts adjusted with prebuffer to 395230
audio jump, diff=-3601
video jump
play_internal ...done
xine_play
ao_flush (loop running: 1)
start pos is 0, start time is 942444
video_pts = 84603600
audio discontinuity #8, type is 3, disc_off 84603600
waiting for in_discontinuity update #8
video discontinuity #8, type is 3, disc_off 84603600
vpts adjusted with prebuffer to 403770
audio discontinuity #9, type is 3, disc_off 84603600
waiting for in_discontinuity update #9
video discontinuity #9, type is 3, disc_off 84603600
vpts adjusted with prebuffer to 404726
audio jump, diff=-1800
video jump
play_internal ...done
xine_play
ao_flush (loop running: 1)
start pos is 0, start time is 1065371
video_pts = 95824800
audio discontinuity #10, type is 3, disc_off 95824800
waiting for in_discontinuity update #10
video discontinuity #10, type is 3, disc_off 95824800
vpts adjusted with prebuffer to 413153
video discontinuity #11, type is 3, disc_off 95822999
waiting for audio discontinuity #11
audio discontinuity #11, type is 3, disc_off 95822999
waiting for in_discontinuity update #11
vpts adjusted with prebuffer to 413159
audio jump, diff=0
video jump
play_internal ...done
xine_play
ao_flush (loop running: 1)
start pos is 0, start time is 1116591
video_pts = 100170000
audio discontinuity #12, type is 3, disc_off 100170000
waiting for in_discontinuity update #12
video discontinuity #12, type is 3, disc_off 100170000
vpts adjusted with prebuffer to 422466
audio discontinuity #13, type is 3, disc_off 100170000
waiting for in_discontinuity update #13
video discontinuity #13, type is 3, disc_off 100170000
vpts adjusted with prebuffer to 423672
audio jump, diff=-1800
video jump
play_internal ...done
xine_play
ao_flush (loop running: 1)
start pos is 0, start time is 1126835
video_pts = 100731600
audio discontinuity #14, type is 3, disc_off 100731600
waiting for in_discontinuity update #14
video discontinuity #14, type is 3, disc_off 100731600
vpts adjusted with prebuffer to 432854
video discontinuity #15, type is 3, disc_off 100729800
waiting for audio discontinuity #15
audio discontinuity #15, type is 3, disc_off 100729800
waiting for in_discontinuity update #15
vpts adjusted with prebuffer to 432859
audio jump, diff=-3600
video jump
play_internal ...done
200 frames delivered, 11 frames skipped, 0 frames discarded
ao_flush (loop running: 1)
input_cache: read calls: 4608, main input read calls: 4580
input_cache: seek_calls: 4640, main input seek calls: 4598
xine_dispose
shutdown audio
ao_close
audio_out: no streams left, closing driver
shutdown video
xine_exit: bye!

```

Can anybody make sense of what is happening here?

---

### Post by misha1983 on 2008-05-10
Here's what would have worked with an older version of Totem:  [http://ubuntuforums.org/showthread.php?t=170305](http://ubuntuforums.org/showthread.php?t=170305)

However, with the newer Totem, it seems the configuration is now accessible through the gconf-editor instead.  I can't see a way to set the audio driver to use from within gconf-editor -- does anyone know how to do it?

---

### Post by Mikebo on 2008-07-07
I have a similar problem. Switched from totem-gstreamer to totem-xine, because gstreamer couldn't handle some video streams wich xine does perfectly. But the problem is that i can't listen to anything else while using totem-xine and vice versa. I've configured xine (~/.xine/config) to use alsa and with the xine player it seems to do so but totem-xine and gxine don't respect that setting, what makes me think that this is a xine player setting and not xine backend (which i imagine would be more like ~/.libxine/config) but maybe i'm wrong. Anyway something i f*cked again and we need help.:wink:

edit:
Ok I did some reading on xinehq.de and it turns out that ~/.xine/config applies only to xine player same way ~/.gxine/config applies to gxine player. So what we need is to configure totem-xine to use alsa, i don't know yet how but there must be a way.

edit:
SOLVED: ```
gedit ~/.config/totem/xine_config
```
replace ```
#audio.driver:auto
``` with ```
audio.driver:alsa
```

First time i've fixed something on my own :guitar: hope this gonna help you as well.

I just discovered that vlc wasn't using alsa either, to fix it i did this:
```
gedit ~/.vlc/vlcrc
```
replace ```
#aout=
```
with ```
aout=alsa
```

---

