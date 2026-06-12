---
title: "Ubuntu - Deadbeef locking up/freezing"
date: 2013-10-29
forum: Multimedia Software
---

### Post by mark_E on 2013-10-29
Hi all,

Have returned to ubuntu with release of 13.10 (and a resonable laptop) and really liking it. I have a problem with deadbeef (0.5.6.1) installed from starws ppa. Deadbeef plugins are also installed.

[EDIT] This is all 64bit.

Deadbeef is freezing up when attempting to add/open files or when closing the preferences dialog (and on other occassions). 

This is (obviously) a fairly fresh ubuntu install and fully updated. I've run this version of deadbeef on other distros without issue so seems to be an ubuntu/unity/gtk3 (?) issue. Perhaps deadbeef developers need to update specifically for 13.10? Have returned system theming changes back to default and tried other versions of deadbeef.

Anyone else have this issue or am I just extra special? ;) Any help appreciated.

What follows is terminal output when run from terminal. At this point it's locked up after trying to add a file

```

starting deadbeef 0.5.6
server_start
loading plugins from /home/gurtid/.local/lib/deadbeef
loading plugins from /usr/lib/deadbeef
plug_load_all: scandir found 135 files
loading plugin /usr/lib/deadbeef/aac.so
loading plugin /usr/lib/deadbeef/adplug.so
loading plugin /usr/lib/deadbeef/alac.so
loading plugin /usr/lib/deadbeef/alsa.so
loading plugin /usr/lib/deadbeef/artwork.so
loading plugin /usr/lib/deadbeef/cdda.so
loading plugin /usr/lib/deadbeef/converter.so
loading plugin /usr/lib/deadbeef/converter_gtk2.so
loading plugin /usr/lib/deadbeef/converter_gtk3.so
loading plugin /usr/lib/deadbeef/dca.so
loading plugin /usr/lib/deadbeef/ddb_ao.so
loading plugin /usr/lib/deadbeef/ddb_dumb.so
found gui plugin ddb_gui_GTK2.so
added GTK2 gui plugin
found gui plugin ddb_gui_GTK3.so
added GTK3 gui plugin
loading plugin /usr/lib/deadbeef/ddb_mono2stereo.so
loading plugin /usr/lib/deadbeef/ddb_shn.so
loading plugin /usr/lib/deadbeef/dsp_libsrc.so
loading plugin /usr/lib/deadbeef/ffap.so
loading plugin /usr/lib/deadbeef/ffmpeg.so
loading plugin /usr/lib/deadbeef/flac.so
loading plugin /usr/lib/deadbeef/gme.so
loading plugin /usr/lib/deadbeef/hotkeys.so
loading plugin /usr/lib/deadbeef/lastfm.so
loading plugin /usr/lib/deadbeef/m3u.so
loading plugin /usr/lib/deadbeef/mms.so
loading plugin /usr/lib/deadbeef/mpgmad.so
loading plugin /usr/lib/deadbeef/musepack.so
loading plugin /usr/lib/deadbeef/notify.so
loading plugin /usr/lib/deadbeef/nullout.so
loading plugin /usr/lib/deadbeef/oss.so
loading plugin /usr/lib/deadbeef/pulse.so
loading plugin /usr/lib/deadbeef/shellexec.so
loading plugin /usr/lib/deadbeef/shellexecui_gtk2.so
loading plugin /usr/lib/deadbeef/shellexecui_gtk3.so
loading plugin /usr/lib/deadbeef/sid.so
loading plugin /usr/lib/deadbeef/sndfile.so
loading plugin /usr/lib/deadbeef/supereq.so
loading plugin /usr/lib/deadbeef/tta.so
loading plugin /usr/lib/deadbeef/vfs_curl.so
loading plugin /usr/lib/deadbeef/vfs_zip.so
loading plugin /usr/lib/deadbeef/vorbis.so
loading plugin /usr/lib/deadbeef/vtx.so
loading plugin /usr/lib/deadbeef/wavpack.so
loading plugin /usr/lib/deadbeef/wildmidi.so
checking GUI plugin: GTK2
found selected GUI plugin: GTK2
loading plugin /usr/lib/deadbeef/ddb_gui_GTK2.so
gtkui plugin compiled for gtk version: 2.24.20
connecting button tray signals
selected output plugin: ALSA output plugin
INFO: loading playlist Default
INFO: from file /home/gurtid/.config/deadbeef/playlists/0.dbpl
convgui: gtkui plugin not found
plugin Converter GTK3 UI failed to connect to dependencies, deactivated.
plugin Shellexec GTK3 UI failed to connect to dependencies, deactivated.
gtkui: found cover-art loader plugin

```

---

### Post by mark_E on 2013-10-30
Update: this is a deadbeef bug to be fixed in the .6 release (although is fixed under current betas - currently at beta 6)

---

