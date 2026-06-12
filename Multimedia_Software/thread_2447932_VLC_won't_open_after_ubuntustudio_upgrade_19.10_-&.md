---
title: "VLC won't open after ubuntustudio upgrade 19.10 -&gt; 20.04"
date: 2020-07-29
forum: Multimedia Software
---

### Post by joebuntu99 on 2020-07-29
After upgrading my ubuntu system to the latest LTS version 20.04 VLC no longer opens.

Running the command vlc from terminal gives the following message

```
VLC media player 3.0.9.2 Vetinari (revision 3.0.9.2-0-gd4c1aefe4d)
Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 541: elf_machine_rela_relative: Assertion `ELFW(R_TYPE) (reloc->r_info) == R_X86_64_RELATIVE' failed!
```


I have attempted to turn on logging to see if I can gain more information using the command
```
vlc --file-logging --log-verbose=2 --logfile=~/vlc.start.log
```
However I simply receive the same message and no log is created.

Searches for the error message reveal a few similar issues but most are very old. I suspect a shared library is to blame, perhaps a codec or driver of some sort but I require help diagnosing the issue.

I have uninstalled vlc and dependencies and reinstalled but the issue remains. Apt showed an issue with plugins and suggested I manually run
```
/usr/lib/x86_64-linux-gnu/vlc/vlc-cache-gen /usr/lib/x86_64-linux-gnu/vlc/plugins
```
I did this and received the same error message.

(I can sucessfully install a working snap of vlc but I do not wish to use snaps on my system if they can be avoided.)
Any help or advice appreciated, thanks.

---

### Post by collisiondomain on 2020-07-29
Try installing the debsums package and then run ```
debsums vlc
``` That will check the MD5 sums of the VLC files to see if any are corrupt.

---

### Post by joebuntu99 on 2020-07-29
Thanks for your response

```
debsums vlc
/usr/lib/mime/packages/vlc                                                    OK
/usr/share/applications/vlc.desktop                                           OK
/usr/share/bug/vlc/control                                                    OK
/usr/share/bug/vlc/presubj                                                    OK
/usr/share/doc/vlc/AUTHORS.gz                                                 OK
/usr/share/doc/vlc/README                                                     OK
/usr/share/doc/vlc/THANKS.gz                                                  OK
/usr/share/doc/vlc/copyright                                                  OK
/usr/share/lintian/overrides/vlc                                              OK
/usr/share/metainfo/vlc.appdata.xml                                           OK
/usr/share/solid/actions/vlc-openbd.desktop                                   OK
/usr/share/solid/actions/vlc-opencda.desktop                                  OK
/usr/share/solid/actions/vlc-opendvd.desktop                                  OK
/usr/share/solid/actions/vlc-openvcd.desktop                                  OK
```

---

### Post by collisiondomain on 2020-07-29
What message did apt give you about the plugins? The issue might be (and this is just a guess based on the fact you upgraded the OS) due to version incompatibility between VLC and some of its dependencies rather than package integrity, in which case the message apt gave you about plugins might help.

But to further probe the issue of package integrity, you could try seeing what the dependencies and reverse dependencies of the vlc package are:

```
apt-cache rdepends vlc && apt-cache depends vlc
```

Then you could try verifying the integrity of the installed packages that are for plugins, e.g.:

```
debsums vlc-plugin-base
```

There is an rdebsums package that can check the MD5 sums for all dependencies of a package, but it only seems to be available in Debian, not Ubuntu.

---

### Post by joebuntu99 on 2020-07-29
> **collisiondomain said:**
> What message did apt give you about the plugins? The issue might be (and this is just a guess based on the fact you upgraded the OS) due to version incompatibility between VLC and some of its dependencies rather than package integrity, in which case the message apt gave you about plugins might help.

The command ```
sudo apt install --reinstall vlc-bin vlc-plugin-base vlc-plugin-qt vlc-plugin-video-output
```
Outputs
```
...
Setting up vlc-bin (3.0.9.2-1) ...
Setting up vlc-plugin-qt:amd64 (3.0.9.2-1) ...
Setting up vlc-plugin-base:amd64 (3.0.9.2-1) ...
Setting up vlc-plugin-video-output:amd64 (3.0.9.2-1) ...
Processing triggers for libvlc-bin:amd64 (3.0.9.2-1) ...
Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 541: elf_machine_rela_relative: Assertion `ELFW(R_TYPE) (reloc->r_info
) == R_X86_64_RELATIVE' failed!
WARNING: Regenerating VLC plugin cache failed.
Please run '/usr/lib/x86_64-linux-gnu/vlc/vlc-cache-gen /usr/lib/x86_64-linux-gnu/vlc/plugins' manually.

```

when I run the suggested command 
```
/usr/lib/x86_64-linux-gnu/vlc/vlc-cache-gen /usr/lib/x86_64-linux-gnu/vlc/plugins
```
I get the initial error message
```
Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 541: elf_machine_rela_relative: Assertion `ELFW(R_TYPE) (reloc->r_info) == R_X86_64_RELATIVE' failed!
```

> 
```
apt-cache rdepends vlc && apt-cache depends vlc
```


```
apt-cache rdepends vlc
vlc
Reverse Depends:
  cinnamon-desktop-environment
 |vokoscreen
  vlc-plugin-visualization
  vlc-plugin-video-splitter
  vlc-plugin-video-output
  vlc-plugin-svg
  vlc-plugin-skins2
  vlc-plugin-samba
  vlc-plugin-notify
  vlc-plugin-jack
  vlc-plugin-fluidsynth
  vlc-plugin-bittorrent
  vlc-plugin-access-extra
  streamtuner2
 |streamlink
 |smtube
  python3-vlc
 |python3-mecavideo
  playerctl
 |pidgin-mpris
  obs-plugins
  multimedia-players
  multimedia-broadcasting
 |mediathekview
 |lxde
  lubuntu-desktop
  kubuntu-desktop
  junior-video
  hdhomerun-config-gui
 |gaupol
  freetuxtv
  forensics-extra-gui
  ezgo-multimedia
 |emms

```

```
apt-cache depends vlc
vlc
  Depends: vlc-bin
  Depends: vlc-plugin-base
  Depends: vlc-plugin-qt
  Depends: vlc-plugin-video-output
  Recommends: vlc-l10n
  Recommends: vlc-plugin-notify
  Recommends: vlc-plugin-samba
  Recommends: vlc-plugin-skins2
  Recommends: vlc-plugin-video-splitter
  Recommends: vlc-plugin-visualization

```

> Then you could try verifying the integrity of the installed packages that are for plugins, e.g.:

```
debsums vlc-plugin-base
```

These all verify ok

```
debsums vlc-plugin-base
/usr/lib/x86_64-linux-gnu/vlc/libvlc_pulse.so.0.0.0                           OK
/usr/lib/x86_64-linux-gnu/vlc/lua/extensions/VLSub.luac                       OK
/usr/lib/x86_64-linux-gnu/vlc/lua/intf/cli.luac                               OK
/usr/lib/x86_64-linux-gnu/vlc/lua/intf/dummy.luac                             OK
/usr/lib/x86_64-linux-gnu/vlc/lua/intf/dumpmeta.luac                          OK
/usr/lib/x86_64-linux-gnu/vlc/lua/intf/http.luac                              OK
/usr/lib/x86_64-linux-gnu/vlc/lua/intf/luac.luac                              OK
/usr/lib/x86_64-linux-gnu/vlc/lua/intf/modules/host.luac                      OK
/usr/lib/x86_64-linux-gnu/vlc/lua/intf/modules/httprequests.luac              OK
/usr/lib/x86_64-linux-gnu/vlc/lua/intf/telnet.luac                            OK
/usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac                OK
/usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac                OK
/usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac                   OK
/usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac                     OK
/usr/lib/x86_64-linux-gnu/vlc/lua/meta/reader/filename.luac                   OK
/usr/lib/x86_64-linux-gnu/vlc/lua/modules/common.luac                         OK
/usr/lib/x86_64-linux-gnu/vlc/lua/modules/dkjson.luac                         OK
/usr/lib/x86_64-linux-gnu/vlc/lua/modules/sandbox.luac                        OK
/usr/lib/x86_64-linux-gnu/vlc/lua/modules/simplexml.luac                      OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/anevia_streams.luac                OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/anevia_xml.luac                    OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/appletrailers.luac                 OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/bbc_co_uk.luac                     OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/cue.luac                           OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/dailymotion.luac                   OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/jamendo.luac                       OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/koreus.luac                        OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/liveleak.luac                      OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/newgrounds.luac                    OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/rockbox_fm_presets.luac            OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/soundcloud.luac                    OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/twitch.luac                        OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/vimeo.luac                         OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/vocaroo.luac                       OK
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/youtube.luac                       OK
/usr/lib/x86_64-linux-gnu/vlc/lua/sd/icecast.luac                             OK
/usr/lib/x86_64-linux-gnu/vlc/lua/sd/jamendo.luac                             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libaccess_alsa_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libaccess_concat_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libaccess_imem_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libaccess_mms_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libaccess_mtp_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libaccess_realrtsp_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libattachment_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libavio_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libcdda_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libdc1394_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libdtv_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libdv1394_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libdvb_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libdvdnav_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libdvdread_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libfilesystem_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libftp_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libhttp_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libhttps_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libidummy_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libimem_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/liblibbluray_plugin.so           OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/liblinsys_hdsdi_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/liblinsys_sdi_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/liblive555_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libnfs_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libpulsesrc_plugin.so            OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/librtp_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libsatip_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libsdp_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libsftp_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libshm_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libtcp_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libtimecode_plugin.so            OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libudp_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libv4l2_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libvcd_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access/libvdr_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access_output/libaccess_output_dummy_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access_output/libaccess_output_file_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access_output/libaccess_output_http_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access_output/libaccess_output_livehttp_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access_output/libaccess_output_shout_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access_output/libaccess_output_srt_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/access_output/libaccess_output_udp_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libaudio_format_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libaudiobargraph_a_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libchorus_flanger_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libcompressor_plugin.so    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libdolby_surround_decoder_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libequalizer_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libgain_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libheadphone_channel_mixer_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libkaraoke_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libmad_plugin.so           OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libmono_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libnormvol_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libparam_eq_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libremap_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libsamplerate_plugin.so    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libscaletempo_pitch_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libscaletempo_plugin.so    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libsimple_channel_mixer_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libsoxr_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libspatialaudio_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libspatializer_plugin.so   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libspeex_resampler_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libstereo_widen_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libtospdif_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libtrivial_channel_mixer_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_filter/libugly_resampler_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_mixer/libfloat_mixer_plugin.so    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_mixer/libinteger_mixer_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_output/libadummy_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_output/libafile_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_output/libalsa_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_output/libamem_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_output/libpulse_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/audio_output/libsndio_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/liba52_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libadpcm_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libaes3_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libaom_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libaraw_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libaribsub_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libavcodec_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libcc_plugin.so                   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libcdg_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libcvdsub_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libdca_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libddummy_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libdvbsub_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libedummy_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libfaad_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libflac_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libg711_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libjpeg_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libkate_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/liblibass_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/liblibmpeg2_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/liblpcm_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libmpg123_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/liboggspots_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libomxil_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libopus_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libpng_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/librawvideo_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/librtpvideo_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libscte18_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libscte27_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libsdl_image_plugin.so            OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libshine_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libspdif_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libspeex_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libspudec_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libstl_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libsubsdec_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libsubstx3g_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libsubsusf_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libsvcdsub_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libsvgdec_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libt140_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libtextst_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libtheora_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libttml_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libtwolame_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libuleaddvaudio_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libvaapi_drm_plugin.so            OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libvaapi_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libvorbis_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libwebvtt_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libx26410b_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libx264_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libx265_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libxwd_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/libzvbi_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/control/libdbus_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/control/libdummy_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/control/libgestures_plugin.so           OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/control/libhotkeys_plugin.so            OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/control/liblirc_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/control/libmotion_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/control/libnetsync_plugin.so            OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/control/liboldrc_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/control/libxcb_hotkeys_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libadaptive_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libaiff_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libasf_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libau_plugin.so                   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libavformat_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libavi_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libcaf_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libdemux_cdg_plugin.so            OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libdemux_chromecast_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libdemux_stl_plugin.so            OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libdemuxdump_plugin.so            OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libdiracsys_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libdirectory_demux_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libes_plugin.so                   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libflacsys_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libh26x_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libimage_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libmjpeg_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libmkv_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libmod_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libmp4_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libmpc_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libmpgv_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libnoseek_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libnsc_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libnsv_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libnuv_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libogg_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libplaylist_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libps_plugin.so                   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libpva_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawaud_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawdv_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawvid_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libreal_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libsid_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libsmf_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libsubtitle_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libts_plugin.so                   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libtta_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libty_plugin.so                   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libvc1_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libvobsub_plugin.so               OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libvoc_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libwav_plugin.so                  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/libxa_plugin.so                   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/gui/libncurses_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/keystore/libfile_keystore_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/keystore/libkwallet_plugin.so           OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/keystore/libmemory_keystore_plugin.so   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/keystore/libsecret_plugin.so            OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/logger/libconsole_logger_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/logger/libfile_logger_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/logger/libsd_journal_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/logger/libsyslog_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/lua/liblua_plugin.so                    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/meta_engine/libfolder_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/meta_engine/libtaglib_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/libaddonsfsstorage_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/libaddonsvorepository_plugin.so    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/libaudioscrobbler_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/libdbus_screensaver_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/libexport_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/libfingerprinter_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/libgnutls_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/liblogger_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/libstats_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/libvod_rtsp_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/libxdg_screensaver_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/misc/libxml_plugin.so                   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/mux/libmux_asf_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/mux/libmux_avi_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/mux/libmux_dummy_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/mux/libmux_mp4_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/mux/libmux_mpjpeg_plugin.so             OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/mux/libmux_ogg_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/mux/libmux_ps_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/mux/libmux_ts_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/mux/libmux_wav_plugin.so                OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_a52_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_av1_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_avparser_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_copy_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_dirac_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_dts_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_flac_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_h264_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_hevc_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_mlp_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_mpeg4audio_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_mpeg4video_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_mpegaudio_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_mpegvideo_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/packetizer/libpacketizer_vc1_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/services_discovery/libavahi_plugin.so   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/services_discovery/libmediadirs_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/services_discovery/libmtp_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/services_discovery/libpodcast_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/services_discovery/libpulselist_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/services_discovery/libsap_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/services_discovery/libudev_plugin.so    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/services_discovery/libupnp_plugin.so    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/services_discovery/libxcb_apps_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/spu/libaudiobargraph_v_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/spu/libdynamicoverlay_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/spu/liblogo_plugin.so                   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/spu/libmarq_plugin.so                   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/spu/libmosaic_plugin.so                 OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/spu/libremoteosd_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/spu/librss_plugin.so                    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/spu/libsubsdelay_plugin.so              OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_extractor/libarchive_plugin.so   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_filter/libadf_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_filter/libcache_block_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_filter/libcache_read_plugin.so   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_filter/libdecomp_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_filter/libhds_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_filter/libinflate_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_filter/libprefetch_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_filter/librecord_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_filter/libskiptags_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_autodel_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_bridge_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_chromaprint_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_chromecast_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_cycle_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_delay_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_description_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_display_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_dummy_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_duplicate_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_es_plugin.so   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_gather_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_mosaic_bridge_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_record_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_rtp_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_setid_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_smem_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_standard_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_stats_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/stream_out/libstream_out_transcode_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/text_renderer/libfreetype_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/text_renderer/libtdummy_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libchain_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libgrey_yuv_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi420_10_p010_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi420_nv12_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi420_rgb_mmx_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi420_rgb_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi420_rgb_sse2_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi420_yuy2_mmx_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi420_yuy2_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi420_yuy2_sse2_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi422_i420_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi422_yuy2_mmx_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi422_yuy2_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libi422_yuy2_sse2_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/librv32_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libswscale_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libyuvp_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libyuy2_i420_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_chroma/libyuy2_i422_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libadjust_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libalphamask_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libanaglyph_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libantiflicker_plugin.so   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libball_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libblend_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libblendbench_plugin.so    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libbluescreen_plugin.so    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libcanvas_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libcolorthres_plugin.so    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libcroppadd_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libdeinterlace_plugin.so   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libedgedetection_plugin.so OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/liberase_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libextract_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libfps_plugin.so           OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libfreeze_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libgaussianblur_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libgradfun_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libgradient_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libgrain_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libhqdn3d_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libinvert_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libmagnify_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libmirror_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libmotionblur_plugin.so    OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libmotiondetect_plugin.so  OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/liboldmovie_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libposterize_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libpostproc_plugin.so      OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libpsychedelic_plugin.so   OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libpuzzle_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libripple_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/librotate_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libscale_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libscene_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libsepia_plugin.so         OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libsharpen_plugin.so       OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libtransform_plugin.so     OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libvhs_plugin.so           OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_filter/libwave_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_output/libfb_plugin.so            OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_output/libvdummy_plugin.so        OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_output/libvmem_plugin.so          OK
/usr/lib/x86_64-linux-gnu/vlc/plugins/video_output/libyuv_plugin.so           OK
/usr/share/bug/vlc-plugin-base/control                                        OK
/usr/share/bug/vlc-plugin-base/presubj                                        OK
/usr/share/doc/vlc-plugin-base/copyright                                      OK
/usr/share/lintian/overrides/vlc-plugin-base                                  OK

```

---

### Post by collisiondomain on 2020-07-29
What output do you get if you try to debug VLC with strace?

```
strace vlc
```

---

### Post by joebuntu99 on 2020-07-29
> **collisiondomain said:**
> What output do you get if you try to debug VLC with strace?

```
strace vlc
```

[https://paste.ubuntu.com/p/8qqgSVbx8R/](https://paste.ubuntu.com/p/8qqgSVbx8R/)

---

### Post by collisiondomain on 2020-07-29
There seem to be quite a few places where VLC is trying to access libraries, but it can't find them:

```
[COLOR=#000000]openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/vlc/tls/haswell/x86_64/libvlc_vdpau.so.0", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)[/COLOR]stat("/usr/lib/x86_64-linux-gnu/vlc/tls/haswell/x86_64", 0x7ffc934dddc0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/vlc/tls/haswell/libvlc_vdpau.so.0", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/vlc/tls/haswell", 0x7ffc934dddc0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/vlc/tls/x86_64/libvlc_vdpau.so.0", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/vlc/tls/x86_64", 0x7ffc934dddc0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/vlc/tls/libvlc_vdpau.so.0", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/vlc/tls", 0x7ffc934dddc0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/vlc/haswell/x86_64/libvlc_vdpau.so.0", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/vlc/haswell/x86_64", 0x7ffc934dddc0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/vlc/haswell/libvlc_vdpau.so.0", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/vlc/haswell", 0x7ffc934dddc0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/vlc/x86_64/libvlc_vdpau.so.0", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/vlc/x86_64", 0x7ffc934dddc0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/vlc/libvlc_vdpau.so.0", O_RDONLY|O_CLOEXEC) = 5
read(5, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \"\0\0\0\0\0\0"..., 832) = 832
fstat(5, {st_mode=S_IFREG|0644, st_size=22688, ...}) = 0
mmap(NULL, 24688, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0x7f2873aed000
mmap(0x7f2873aef000, 8192, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x2000) = 0x7f2873aef000
mmap(0x7f2873af1000, 4096, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x4000) = 0x7f2873af1000
mmap(0x7f2873af2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x4000) = 0x7f2873af2000
close(5)                                = 0
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/vlc/libX11.so.6", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 5
fstat(5, {st_mode=S_IFREG|0644, st_size=166528, ...}) = 0
mmap(NULL, 166528, PROT_READ, MAP_PRIVATE, 5, 0) = 0x7f2873ac4000
close(5)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libX11.so.6", O_RDONLY|O_CLOEXEC) = 5
read(5, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\220\1\0\0\0\0\0"..., 832) = 832
fstat(5, {st_mode=S_IFREG|0644, st_size=1293928, ...}) = 0
mmap(NULL, 1297720, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0x7f2873987000
mprotect(0x7f287399f000, 1179648, PROT_NONE) = 0
mmap(0x7f287399f000, 569344, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x18000) = 0x7f287399f000
mmap(0x7f2873a2a000, 606208, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0xa3000) = 0x7f2873a2a000
mmap(0x7f2873abf000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x137000) = 0x7f2873abf000
close(5)                                = 0
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/vlc/libavcodec.so.58", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libavcodec.so.58", O_RDONLY|O_CLOEXEC) = 5
read(5, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\207\7\0\0\0\0\0"..., 832) = 832
```

```
[COLOR=#000000]openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 5[/COLOR]fstat(5, {st_mode=S_IFREG|0644, st_size=166528, ...}) = 0
mmap(NULL, 166528, PROT_READ, MAP_PRIVATE, 5, 0) = 0x7f286ab91000
close(5)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/tls/haswell/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/tls/haswell/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/tls/haswell/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/tls/haswell", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/tls/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/tls/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/tls/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/tls", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/haswell/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/haswell/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/haswell/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/haswell", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu", {st_mode=S_IFDIR|0755, st_size=192512, ...}) = 0
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/tls/haswell/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/tls/haswell/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/tls/haswell/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/tls/haswell", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/tls/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/tls/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/tls/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/tls", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/haswell/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/haswell/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/haswell/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/haswell", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu", {st_mode=S_IFDIR|0755, st_size=192512, ...}) = 0
openat(AT_FDCWD, "/lib/tls/haswell/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/tls/haswell/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/tls/haswell/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/tls/haswell", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/tls/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/tls/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/tls/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/tls", 0x7ffc934dde60)        = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/haswell/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/haswell/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/haswell/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/haswell", 0x7ffc934dde60)    = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64", 0x7ffc934dde60)     = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/lib", {st_mode=S_IFDIR|0755, st_size=20480, ...}) = 0
openat(AT_FDCWD, "/usr/lib/tls/haswell/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls/haswell/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/tls/haswell/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls/haswell", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/tls/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/tls/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls", 0x7ffc934dde60)    = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/haswell/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/haswell/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/haswell/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/haswell", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64", 0x7ffc934dde60) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/libmediaclient.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat("/usr/lib", {st_mode=S_IFDIR|0755, st_size=20480, ...}) = 0
munmap(0x7f286ab91000, 166528)          = 0
```

After you upgraded the OS, were you prompted to update your software by the Software Updater, and if so, did you reboot your computer? If not, does updating your system with the Software Updater and then rebooting affect VLC at all?

---

### Post by joebuntu99 on 2020-07-29
I upgraded on the command line via do-release-upgrade.
I have rebooted and updated with apt several times since.
I used Software Updater to update just now and rebooted. No change.

Only thing I can think of, though I am not suggesting this is (or isn't) connected...
I need to use an old version of Deluge (1.3.15) so that it matches the old (but latest) version of deluged (1.3.15) on my headless raspberry pi running Buster and can be used in Thin Client mode. As such I have Deluge pinned not to update like so
```
/etc/apt/preferences.d/pin-deluge

Package: deluge
Pin: version 1.3.15-2
Pin-Priority: 1337

Package: deluge-common
Pin: version 1.3.15-2
Pin-Priority: 1337

Package: deluge-gtk
Pin: version 1.3.15-2
Pin-Priority: 1337
```

When updating through terminal the system (apt or dpkg I suppose) wanted to uninstall some software including my old version of deluge so to prevent that I set selections in dpkg for deluge to hold so the command
```
dpkg --get-selections | grep deluge
```
gives
```
deluge                        hold
deluge-common                    hold
deluge-gtk                    hold
```

Now when I do an apt update I find the package libtorrent-rasterbar9 is available for update but is then held back.

```
 apt policy libtorrent-rasterbar9
libtorrent-rasterbar9:
  Installed: 1.1.13-1
  Candidate: 1.1.13-1.1build2
  Version table:
     1.1.13-1.1build2 500
        500 http://ie.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
 *** 1.1.13-1 100
        100 /var/lib/dpkg/status

```

But now I am investigating with the new tools you've given me, perhaps this is connected...

```
apt-cache depends libtorrent-rasterbar9
libtorrent-rasterbar9
  Depends: libc6
  Depends: libgcc-s1
  Depends: libssl1.1
  Depends: libstdc++6
  Suggests: libtorrent-rasterbar-dbg

```

```
apt-cache rdepends libtorrent-rasterbar9
libtorrent-rasterbar9
Reverse Depends:
  python-libtorrent
  libtorrent-rasterbar-dbg
  vlc-plugin-bittorrent
  qbittorrent-nox
  qbittorrent
  python3-libtorrent-dbg
  python3-libtorrent
  libtorrent-rasterbar-dev
  btfs
```

As it appears (if I am reading correctly) libtorrent-rasterbar9 is a dependency of vlc-plugin-bittorrent ?

Maybe I should let apt remove deluge and just reinstall it from the deb manually later?

---

### Post by collisiondomain on 2020-07-29
> **joebuntu99 said:**
> As it appears (if I am reading correctly) libtorrent-rasterbar9 is a dependency of vlc-plugin-bittorrent ?

I believe so, yes.

> **joebuntu99 said:**
> Maybe I should let apt remove deluge and just reinstall it from the deb manually later?

It's worth a shot.

If that doesn't work, you could also see if removing vlc-plugin-bittorrent affects how the program runs (unless it has important reverse dependencies you don't want to remove). Conceivably, vlc-plugin-bittorrent might want a newer version of libtorrent-rasterbar9, but only the old one is available; in that case, removing the plugin might fix the issue of VLC wanting to access an old library.

---

### Post by joebuntu99 on 2020-07-29
OK, so I changed the selections in dpkg so deluge, deluge-common, deluge-gtk are marked install instead of hold.
I did sudo apt full-upgrade and apt removed deluge and a python-torrent (not exact name) package as part of the upgrade.
I rebooted and vlc is still behaving the same. No updates available through apt or software updater.

Unexpectedly though deluge 1.3.15 is still installed and working normally as far as I can see. I thought it was going to be removed but it hasn't. Anyway perhaps the deluge thing was a red herring.

(further though I don't think it's relevant now the deluge command is not found, but deluge is available through the icon in my dock and through gui menu also)

```
apt policy deluge
deluge:
  Installed: (none)
  Candidate: 1.3.15-2
  Version table:
     2.0.3-2 500
        500 http://ie.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://ie.archive.ubuntu.com/ubuntu focal/universe i386 Packages
     1.3.15-2 1337
        100 /var/lib/dpkg/status

```

---

### Post by collisiondomain on 2020-07-29
Is the error affected at all by removing vlc-plugin-bittorrent?

> **collisiondomain said:**
> If that doesn't work, you could also see if removing vlc-plugin-bittorrent affects how the program runs (unless it has important reverse dependencies you don't want to remove). Conceivably, vlc-plugin-bittorrent might want a newer version of libtorrent-rasterbar9, but only the old one is available; in that case, removing the plugin might fix the issue of VLC wanting to access an old library.

---

### Post by joebuntu99 on 2020-07-29
> **collisiondomain said:**
> Is the error affected at all by removing vlc-plugin-bittorrent?

sorry I missed that earlier post. I've removed vlc-plugin-bittorrent. (Actually libtorrent-rasterbar9 was then unneeded so was removed with apt autoremove).

I've rebooted and there is no change in behaviour for vlc.

---

### Post by collisiondomain on 2020-07-29
Did any other programs stop working or start behaving oddly after upgrading Ubuntu?

---

### Post by joebuntu99 on 2020-07-29
Not that I've noticed apart from MVP Media Player is not opening properly however Parole seems good. Though honestly I don't use either of those much as I prefer VLC.

---

### Post by collisiondomain on 2020-07-29
When you open mpv, does it give you any error message (GUI or command line)?

---

### Post by joebuntu99 on 2020-07-29
When I open MPV it draws the window frame but the frame is never filled in, then the program dies. No error.
The command line exits with a Segmentation Fault

```
mpv Downloads/sparrow.proper.mov 
 (+) Video --vid=1 (*) (h264 1136x640 30.000fps)
 (+) Audio --aid=1 --alang=eng (*) (aac 2ch 44100Hz)
AO: [pulse] 44100Hz stereo 2ch float
VO: [gpu] 1136x640 yuv420p
Segmentation fault (core dumped)
```

---

### Post by collisiondomain on 2020-07-29
What do you get if you run it through strace?

---

### Post by joebuntu99 on 2020-07-29
[https://paste.ubuntu.com/p/mWxdvhhMnT/](https://paste.ubuntu.com/p/mWxdvhhMnT/)

(thanks so much for all your effort btw)

---

### Post by monkeybrain20122 on 2020-07-29
It would take you less time to backup your data and do a clean install. Even if you fix your vlc problem with some hacks it might just be a symptom and there may be other problems which has yet to surface. I never trust "upgrade" as my system is sufficiently non standard.

---

### Post by collisiondomain on 2020-07-29
For some people, this issue seems to be due to graphic card drivers. One person ([https://ubuntuforums.org/showthread.php?t=2298174](https://ubuntuforums.org/showthread.php?t=2298174)) solved it by reinstalling the drivers for their NVIDIA graphic card.

Another person ([https://reddit.com/r/linuxmint/comments/17oat1/halp_with_vlc_flash_and_probably_other_things/]("https://old.reddit.com/r/linuxmint/comments/17oat1/halp_with_vlc_flash_and_probably_other_things/")) said, "Rinstalled the mpeg codecs, flac codecs, libfaad2, nvidia (from google), restarted. Works now, any 1 or combination of those could have fixed it."[COLOR=#404040][FONT=arial]

[/FONT][/COLOR]Someone else ([https://forums.gentoo.org/viewtopic-p-2960309.html#2960309](https://forums.gentoo.org/viewtopic-p-2960309.html#2960309)) fixed a similar problem by renaming some files (although this was in 2005, so may not be applicable anymore).

> It would take you less time to backup your data and do a clean install. Even if you fix your vlc problem with some hacks it might just be a symptom and there may be other problems which has yet to surface. I never trust "upgrade" as my system is sufficiently non standard.

I would agree with this; in my experience, upgrading can cause issues, so I only do clean installs.

---

### Post by joebuntu99 on 2020-07-29
Ok. I'll take your advice. Thanks for your help. I learned a little at least.

---

### Post by collisiondomain on 2020-07-29
> **joebuntu99 said:**
> Ok. I'll take your advice. Thanks for your help. I learned a little at least.

No problem! Sorry I couldn't figure out what the solution was.

---

