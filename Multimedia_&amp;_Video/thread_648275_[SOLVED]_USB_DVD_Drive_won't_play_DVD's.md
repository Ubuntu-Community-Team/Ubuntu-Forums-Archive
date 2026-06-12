---
title: "[SOLVED] USB DVD Drive won't play DVD's"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by henjj on 2007-12-23
Hello, I have a Compaq F572US running 7.1.   I installed all of the necessary codecs to play DVDs and I have no problem playing DVD's through the internal drive on the machine.  But when I connect my external USB DVD drive, DVD's will not play.  I can play music cds in the external USB drive, but for some reason DVD's will not play.  I would like to be able to play DVD's using this external drive instead of having to use my internal drive.

When trying to play DVDs in the external USB drive, I get these messages from Gxine:  "The xine engine failed to start.  No input plugin was found.  Maybe the file does not exist or cannot be accessed, or there is an error in the URL." and "Read error from: /dev/dvd".

The Engine Log states:  
Messsages:
10:42:27 AM: xine: found demuxer plugin: image demux plugin
10:42:27 AM: xine: found input plugin  : file input plugin
10:42:27 AM: xine: cannot find input plugin for MRL [dvd:/]
10:42:27 AM: xine: input plugin cannot open MRL [dvd:/]
10:42:27 AM: xine: found input plugin  : DVD Navigator

Plugin:
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_dxr3_video.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_caca.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_xvmc.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_sputext.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_ao_out_oss.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_file.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_dxr3.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_dxr3.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_spucc.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_lpcm.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_asf.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_mpeg_pes.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_gdk_pixbuf.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_audio_filters.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_audio_filters.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_audio_filters.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_audio_filters.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_tvtime.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_mosaico.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_planar.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_planar.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_planar.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_planar.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_planar.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_planar.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_planar.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_planar.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_planar.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_planar.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_goom.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_visualizations.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_visualizations.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_visualizations.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/post/xineplug_post_switch.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_qt.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_qt.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_mpeg_block.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_speex.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_nsf.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_dxr3_spu.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_stdin_fifo.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_dvd.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_smb.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_xv.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_xv.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_none.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_xshm.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_xshm.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_theora.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_http.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_sputext.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_sdl.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_mpeg2.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_vcdo.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_mpeg_elem.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_ao_out_esd.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_iff.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_net.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_a52.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_yuv4mpeg2.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_mpc.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_pvr.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_yuv_frames.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_gnome_vfs.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_nsv.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_yuv.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_gsm610.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_directfb.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_ao_out_none.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_mng.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_dvb.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_real.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_vcd.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_mpeg.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_xcbxv.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_avi.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_real.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_real.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_mad.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_vorbis.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_xxmc.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_spucmml.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_faad.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_slave.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_spu.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_matroska.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_dts.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_ao_out_pulseaudio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_flac.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_flac.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_bitplane.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_v4l.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_v4l.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_ao_out_alsa.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_audio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_rgb.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_flv.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_ff.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_ff.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_ff.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_ff.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_syncfb.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_fb.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_ogg.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_ogg.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_w32dll.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_w32dll.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_pva.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_xcbshm.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_image.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_mms.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_rtsp.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_xdirectfb.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_xdirectfb.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_games.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_games.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_games.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_games.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_games.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_games.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_games.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_games.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_games.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_games.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_games.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_fli.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_spudvb.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_decode_dvaudio.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_mpeg_ts.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_dmx_rawdv.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_aa.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_inp_rtp.so found
10:42:26 AM: load_plugins: plugin /usr/lib/xine/plugins/1.1.8/xineplug_vo_out_opengl.so found

Again, I have no problems playing DVD's in my internal DVD drive, but for some reason, they will not play in my external USB DVD drive.  Any help or ideas would be appreciated.  Thanks

---

### Post by Ehtetur on 2007-12-23
> **henjj said:**
> When trying to play DVDs in the external USB drive, I get these messages from Gxine:  "The xine engine failed to start.  No input plugin was found.  Maybe the file does not exist or cannot be accessed, or there is an error in the URL." and "Read error from: /dev/dvd".

It sounds like gxine is trying to play your internal DVD player.
See what you get when you try this:
> ls -l /dev/dvd

When HAL detects the USB DVD, it creates a link to the device in the /media folder and you'll see a shortcut created on your desktop to the USB DVD.
Have gxine play that instead of /dev/dvd.

---

### Post by henjj on 2007-12-24
Thanks for the help!  It worked when I pointed Gxine to play dvd1 instead of dvd in the preferences section.  I appreciate your help.:)

---

