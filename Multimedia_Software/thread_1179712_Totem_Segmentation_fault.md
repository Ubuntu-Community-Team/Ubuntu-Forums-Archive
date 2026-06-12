---
title: "Totem Segmentation fault"
date: 2009-06-05
forum: Multimedia Software
---

### Post by BopNiblets on 2009-06-05
Well I noticed my video thumbnails weren't being generated for new files, so I deleted the .thumbnails folder in Home and hoped Totem would regenerate them, but nothing happened, so then I ran Totem but it just flicked closed immediately, ran in terminal and BAM: "Segmentation fault" :(

Tried reinstall with Package Manager, no change, tried completely remove and install again, no change.

I've recently installed Audacious2, would that have anything to do with it?

Here's debug if it helps:
```
totem --debug
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_dvaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_spucc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_http.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_dxr3_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_mpeg_block.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_vorbis.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_ogg.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_lpcm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_avi.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_gnome_vfs.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xvmc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_mng.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_ao_out_file.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_dvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_mpeg_ts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_yuv4mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_mad.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_spudvb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_sdl.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_net.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_mpeg_pes.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xcbshm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_vcd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_pnm.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_pva.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_image.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_dts.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_ao_out_esd.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_rtp.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xdirectfb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xdirectfb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_switch.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_tvtime.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_goom.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/post/xineplug_post_mosaico.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_ao_out_pulseaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_gdk_pixbuf.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_fb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xcbxv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_spucmml.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_yuv_frames.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_smb.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_vcdo.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_real.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_vo_out_xxmc.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_dmx_nsv.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_inp_mms.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_theora.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_a52.so found
load_plugins: plugin /usr/lib/xine/plugins/1.26/xineplug_decode_faad.so found
Segmentation fault

```

---

