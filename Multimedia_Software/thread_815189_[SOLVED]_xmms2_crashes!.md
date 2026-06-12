---
title: "[SOLVED] xmms2 crashes!"
date: 2008-06-01
forum: Multimedia Software
---

### Post by LinuX-M@n1@k on 2008-06-01
I don't like xmms2, but I decided to give it a shot.

Here's how I installed it:
```
$ sudo apt-get build-dep xmms2 && sudo aptitude install xmms2
```
And here's the problem:
```
$ xmms2d
 INFO: ../src/xmms/log.c:36: Initialized logging system :)
 INFO: ../src/xmms/ipc.c:893: IPC listening on 'unix:///tmp/xmms-ipc-boris'.
 INFO: ../src/xmms/main.c:499: Using output plugin: alsa
[b][i]<now I add a song with `xmms2 add song.mp3`>
<then I try to play it with `xmms2 play`>[/i][/b]
Segmentation fault
***<now I'm smacking my monitor with the keyboard =@>***
$ 
```
What's the problem ? I mean... I know that the problem is - xmms2 crashes (duh), but how do I fix it ?

---

### Post by LinuX-M@n1@k on 2008-06-01
bump

---

### Post by LinuX-M@n1@k on 2008-06-01
Thank you for helping me =@@@

---

### Post by kellemes on 2008-06-01
> **LinuX-M@n1@k said:**
> Thank you for helping me =@@@

A million of people may read your post but none may have the answer  you seek.

---

### Post by steveneddy on 2008-06-01
Uninstall xmms2 and install audacious

---

### Post by LinuX-M@n1@k on 2008-06-01
Okay, here's more info:
```
$ xmms2d --verbose
 INFO: ../src/xmms/log.c:36: Initialized logging system :)
 INFO: ../src/xmms/ipc.c:904: IPC listening on 'unix:///tmp/xmms-ipc-boris'.
DEBUG: ../src/xmms/ipc.c:920: IPC setup done.
DEBUG: ../src/xmms/plugin.c:347: Scanning directory for plugins (/usr/local/lib/xmms2/lib*.so)
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_cdda.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'cdda'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_avformat.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'avformat'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'amr header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_pls.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'pls'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_vocoder.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'vocoder'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_lastfm.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'lastfm'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_jack.so
DEBUG: ../src/xmms/outputplugin.c:93: Registering output 'jack'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_file.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'file'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_id3v2.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'id3v2'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'id3 header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'id3 header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'id3 header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_sid.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'sid'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'sidplay infofile'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'psid header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'rsid header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_rss.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'rss'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_nulstripper.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'nulstripper'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'NUL padded'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_wave.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'wave'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'wave header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'wave header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'wave header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_icymetaint.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'icymetaint'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_asx.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'asx'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'ASX header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_diskwrite.so
DEBUG: ../src/xmms/outputplugin.c:93: Registering output 'diskwrite'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_ao.so
DEBUG: ../src/xmms/outputplugin.c:93: Registering output 'ao'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_xml.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'xml'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'xml header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'xml header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_modplug.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'modplug'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'Fasttracker II module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'ScreamTracker III module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'Impulse Tracker module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'MED module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'Unreal Engine package'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree '4-channel Protracker module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree '4-channel Protracker module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree '4-channel Startracker module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree '8-channel Startracker module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree '4-channel Fasttracker module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree '6-channel Fasttracker module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree '8-channel Fasttracker module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree '8-channel Octalyzer module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree '8-channel Octalyzer module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree '16-channel Taketracker module'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree '32-channel Taketracker module'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_avcodec.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'avcodec'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_mp4.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'mp4'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'mpeg-4 header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'mpeg-4 header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'mpeg-4 header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'mpeg-4 header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'iTunes header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'iTunes header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_alsa.so
DEBUG: ../src/xmms/outputplugin.c:93: Registering output 'alsa'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_mms.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'mms'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_vorbis.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'vorbis'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'ogg/vorbis header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'ogg/vorbis header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'ogg/vorbis header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_curl.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'curl'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_gnomevfs.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'gnomevfs'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_mad.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'mad'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'mpeg header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'mpeg header'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'mpeg header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_daap.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'daap'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_ofa.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'ofa'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_equalizer.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'equalizer'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_lastfmeta.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'lastfmeta'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'SYNC padded'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_normalize.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'normalize'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_oss.so
DEBUG: ../src/xmms/outputplugin.c:93: Registering output 'oss'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_flac.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'flac'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'flac header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_xspf.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'xspf'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_asf.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'asf'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'asf header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_musepack.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'musepack'
DEBUG: ../src/xmms/magic.c:299: adding magic spec to tree 'mpc header'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_cue.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'cue'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_ices.so
DEBUG: ../src/xmms/outputplugin.c:93: Registering output 'ices'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_m3u.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'm3u'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_samba.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'smb'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_replaygain.so
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'replaygain'
DEBUG: ../src/xmms/plugin.c:370: Trying to load file: /usr/local/lib/xmms2/libxmms_null.so
DEBUG: ../src/xmms/outputplugin.c:93: Registering output 'null'
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'ringbuf'
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'magic'
DEBUG: ../src/xmms/xform.c:1149: Registering xform 'converter'
DEBUG: ../src/xmms/sqlite.c:368: xmms_sqlite_create done!
 INFO: ../src/xmms/main.c:493: Using output plugin: alsa
DEBUG: ../src/xmms/output.c:876: Trying to open output
DEBUG: ../src/xmms/output.c:887: Using buffersize 32768
DEBUG: ../src/plugins/alsa/alsa.c:203: Probing device: default
DEBUG: ../src/xmms/main.c:140: Running scripts in /home/boris/.config/xmms2/startup.d
DEBUG: ../src/xmms/mediainfo.c:159: got 0 as not resolved
DEBUG: ../src/xmms/ipc.c:586: Client connected
DEBUG: ../src/xmms/main.c:267: Client 'xmms2-cli' connected
DEBUG: ../src/xmms/playlist.c:194: PLAYLIST: updated chg!
DEBUG: ../src/xmms/mediainfo.c:159: got 29 as not resolved
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1207: Skipping plugin 'ringbuf'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'replaygain'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'smb'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'm3u'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'cue'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'musepack'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'asf'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'xspf'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'flac'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'normalize'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'lastfmeta'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'equalizer'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'ofa'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'daap'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'mad'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'gnomevfs'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'curl'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'vorbis'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'mms'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'mp4'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'avcodec'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'modplug'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'xml'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'asx'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'icymetaint'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'wave'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'nulstripper'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'rss'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'sid'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'id3v2'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'file'
DEBUG: ../src/xmms/xform.c:1213: Plugin 'file' matched
DEBUG: ../src/plugins/file/file.c:114: Opening /home/boris/Downloads/VA-Tunes__Volume_1-3CD-2008-MNS/306-carl_b_pres._khensu-chasing_leaves__original_mix.mp3
DEBUG: ../src/xmms/xform.c:499: Setting 'size' to 13258468
DEBUG: ../src/xmms/xform.c:499: Setting 'lmod' to 1212340933
DEBUG: ../src/xmms/xform.c:1286: Not in one of 1 goal-types
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1213: Plugin 'magic' matched
DEBUG: ../src/xmms/magic.c:460: magic plugin detected 'application/id3v2' (id3 header)
DEBUG: ../src/xmms/xform.c:1286: Not in one of 1 goal-types
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1207: Skipping plugin 'ringbuf'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'replaygain'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'smb'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'm3u'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'cue'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'musepack'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'asf'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'xspf'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'flac'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'normalize'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'lastfmeta'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'equalizer'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'ofa'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'daap'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'mad'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'gnomevfs'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'curl'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'vorbis'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'mms'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'mp4'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'avcodec'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'modplug'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'xml'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'asx'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'icymetaint'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'wave'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'nulstripper'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'rss'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'sid'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'id3v2'
DEBUG: ../src/xmms/xform.c:1213: Plugin 'id3v2' matched
DEBUG: ../src/plugins/id3v2/id3.c:518: Found id3v2 header (version=3, rev=0, len=4086, flags=0)
DEBUG: ../src/xmms/xform.c:499: Setting 'size' to 13254382
DEBUG: ../src/xmms/xform.c:499: Setting 'tracknr' to 26
DEBUG: ../src/plugins/id3v2/id3.c:465: Unhandled tag TENC
DEBUG: ../src/plugins/id3v2/id3.c:465: Unhandled tag TLAN
DEBUG: ../src/xmms/xform.c:1286: Not in one of 1 goal-types
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1213: Plugin 'magic' matched
DEBUG: ../src/xmms/magic.c:460: magic plugin detected 'audio/mpeg' (mpeg header)
DEBUG: ../src/xmms/xform.c:1286: Not in one of 1 goal-types
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1207: Skipping plugin 'ringbuf'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'replaygain'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'smb'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'm3u'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'cue'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'musepack'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'asf'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'xspf'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'flac'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'normalize'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'lastfmeta'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'equalizer'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'ofa'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'daap'
DEBUG: ../src/xmms/xform.c:1211: Trying plugin 'mad'
DEBUG: ../src/xmms/xform.c:1213: Plugin 'mad' matched
DEBUG: ../src/plugins/mad/xing.c:112: LAME tag found!
DEBUG: ../src/plugins/mad/mad.c:271: File with Xing header!
DEBUG: ../src/xmms/xform.c:499: Setting 'isvbr' to 1
DEBUG: ../src/plugins/mad/mad.c:284: XING duration 496222
DEBUG: ../src/xmms/xform.c:499: Setting 'duration' to 496222
DEBUG: ../src/plugins/mad/mad.c:293: XING bitrate 213682
DEBUG: ../src/xmms/xform.c:499: Setting 'bitrate' to 213682
DEBUG: ../src/plugins/mad/mad.c:306: Samples to skip in the beginning: 576, total: 21881244
DEBUG: ../src/plugins/mad/id3v1.c:134: Found ID3v1 TAG!
DEBUG: ../src/xmms/xform.c:499: Setting 'samplerate' to 44100
DEBUG: ../src/xmms/xform.c:499: Setting 'channels' to 2
DEBUG: ../src/xmms/xform.c:611: Collecting metadata from file
DEBUG: ../src/xmms/xform.c:611: Collecting metadata from magic
DEBUG: ../src/xmms/xform.c:611: Collecting metadata from id3v2
DEBUG: ../src/xmms/xform.c:611: Collecting metadata from magic
DEBUG: ../src/xmms/xform.c:611: Collecting metadata from mad
DEBUG: ../src/xmms/ipc.c:387: disconnect was true!
 INFO: ../src/xmms/xform.c:1402: Successfully setup chain for 'file:///home/boris/Downloads/VA-Tunes__Volume_1-3CD-2008-MNS/306-carl_b_pres._khensu-chasing_leaves__original_mix.mp3' (29) containing file:magic:id3v2:magic:mad
DEBUG: ../src/xmms/xform.c:337: Freeing xform 'mad'
DEBUG: ../src/xmms/xform.c:337: Freeing xform 'magic'
DEBUG: ../src/xmms/xform.c:337: Freeing xform 'id3v2'
DEBUG: ../src/xmms/xform.c:337: Freeing xform 'magic'
DEBUG: ../src/xmms/xform.c:337: Freeing xform 'file'
DEBUG: ../src/xmms/xform.c:337: Freeing xform 'unknown'
DEBUG: ../src/xmms/mediainfo.c:159: got 0 as not resolved
DEBUG: ../src/xmms/ipc.c:500: Destroying client!
DEBUG: ../src/xmms/ipc.c:586: Client connected
DEBUG: ../src/xmms/main.c:267: Client 'xmms2-cli' connected
DEBUG: ../src/xmms/outputplugin.c:272: Running status changed... 1
Segmentation fault
$ 
```

> **kellemes said:**
> A million of people may read your post but none may have the answer  you seek.
The last 3 or 4 threads I started no one answered me ! Isn't that luck or what ?

> **steveneddy said:**
> Uninstall xmms2 and install audacious

I want something for the CLI. (As far as I know, Audacious is with GUI ?)

---

### Post by LinuX-M@n1@k on 2008-06-02
Anyone ?
I'm using xmms2 version 0.4 DrKosmos compiled from source.
I need to get it fixed as soon as possible... Any help will be appreciated.
:(

---

### Post by xc3RnbFO8P on 2008-06-02
Try:
> xmms2 **radd** /home/your folder/your music folder (or drag/drop folder in to terminal)
xmms2 play

---

### Post by LinuX-M@n1@k on 2008-06-02
Still crashes!
Output:
```
$ xmms2 radd dcpp
$ xmms2 list
->[0/27] Britney Spears - Piece Of Me (03:32)
  [1/27] Britney Spears - Piece Of Me (03:32)
  [2/27] Britney Spears - Piece Of Me (03:32)
  [3/60] Black Eyed Peas feat. Justin Timberlake - Where Is The Love (03:48)
  [4/59] Eminem - Mockingbird (04:11)
  [5/25] Ice Cube - Right Here, Right Now (04:13)
  [6/61] Metallica - Nothing Else Matters (live) (06:22)

Total playtime: 0:29:10
$ xmms2 play
$ 
```
Output from xmms2d after `xmms2 play`:
```
DEBUG: ../src/xmms/ipc.c:581: Client connected
DEBUG: ../src/xmms/main.c:259: Client xmms2-cli with protocol version 1 sent hello!
DEBUG: ../src/xmms/outputplugin.c:223: Running status changed... 1
DEBUG: ../src/xmms/playlist.c:181: PLAYLIST: updated pos!
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1115: Skipping plugin 'ringbuf'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'replaygain'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'equalizer'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'mad'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'vorbis'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'wave'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'nulstripper'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'id3v2'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'file'
DEBUG: ../src/xmms/xform.c:1121: Plugin 'file' matched
DEBUG: ../src/plugins/file/file.c:113: Opening /home/boris/dcpp/02-britney_spears-piece_of_me.mp3
DEBUG: ../src/xmms/xform.c:481: Setting 'size' to 5151668
DEBUG: ../src/xmms/xform.c:481: Setting 'lmod' to 1209292654
DEBUG: ../src/xmms/xform.c:1182: Not in one of 112 goal-types
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1121: Plugin 'magic' matched
DEBUG: ../src/xmms/magic.c:460: magic plugin detected 'application/id3v2' (id3 header)
DEBUG: ../src/xmms/xform.c:1182: Not in one of 112 goal-types
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1115: Skipping plugin 'ringbuf'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'replaygain'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'equalizer'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'mad'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'vorbis'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'wave'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'nulstripper'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'id3v2'
DEBUG: ../src/xmms/xform.c:1121: Plugin 'id3v2' matched
DEBUG: ../src/plugins/id3v2/id3.c:508: Found id3v2 header (version=3, rev=0, len=2326, flags=0)
DEBUG: ../src/xmms/xform.c:481: Setting 'size' to 5149342
DEBUG: ../src/plugins/id3v2/id3.c:455: Unhandled tag TLAN
DEBUG: ../src/xmms/xform.c:481: Setting 'tracknr' to 2
DEBUG: ../src/plugins/id3v2/id3.c:455: Unhandled tag TDAT
DEBUG: ../src/plugins/id3v2/id3.c:455: Unhandled tag TSSE
DEBUG: ../src/plugins/id3v2/id3.c:455: Unhandled tag TPUB
DEBUG: ../src/xmms/xform.c:1182: Not in one of 112 goal-types
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1121: Plugin 'magic' matched
DEBUG: ../src/xmms/magic.c:460: magic plugin detected 'audio/mpeg' (mpeg header)
DEBUG: ../src/xmms/xform.c:1182: Not in one of 112 goal-types
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1115: Skipping plugin 'ringbuf'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'replaygain'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'equalizer'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'mad'
DEBUG: ../src/xmms/xform.c:1121: Plugin 'mad' matched
DEBUG: ../src/plugins/mad/xing.c:112: LAME tag found!
DEBUG: ../src/plugins/mad/mad.c:270: File with Xing header!
DEBUG: ../src/xmms/xform.c:481: Setting 'isvbr' to 1
DEBUG: ../src/plugins/mad/mad.c:282: XING duration 212166
DEBUG: ../src/xmms/xform.c:481: Setting 'duration' to 212166
DEBUG: ../src/plugins/mad/mad.c:292: XING bitrate 194157
DEBUG: ../src/xmms/xform.c:481: Setting 'bitrate' to 194157
DEBUG: ../src/plugins/mad/mad.c:304: Samples to skip in the beginning: 576, total: 9353904
DEBUG: ../src/plugins/mad/id3v1.c:134: Found ID3v1 TAG!
DEBUG: ../src/xmms/xform.c:481: Setting 'samplerate' to 44100
DEBUG: ../src/xmms/xform.c:481: Setting 'channels' to 2
DEBUG: ../src/plugins/alsa/alsa.c:345: Opening device: default
DEBUG: ../src/xmms/ipc.c:392: disconnect was true!
DEBUG: ../src/xmms/ipc.c:495: Destroying client!
DEBUG: ../src/xmms/xform.c:572: Collecting metadata from file
DEBUG: ../src/xmms/xform.c:572: Collecting metadata from magic
DEBUG: ../src/xmms/xform.c:572: Collecting metadata from id3v2
DEBUG: ../src/xmms/xform.c:572: Collecting metadata from magic
DEBUG: ../src/xmms/xform.c:572: Collecting metadata from mad
Segmentation fault
```
Any other ideas? I think it's the ALSA plugin. With OSS it doesn't crash, but it doesn't start playing either.

***Edit:*** Here's the `xmms2 config_list` ouput for ALSA:
```
$ xmms2 config_list |grep alsa
alsa.mixer_dev = default
alsa.mixer = PCM
alsa.device = default
output.plugin = alsa
$
```

---

### Post by xc3RnbFO8P on 2008-06-02
Did you install **XMMS2 - all plugins** in Synaptic Package Manager?
or read this:
[http://wiki.xmms2.xmms.se/wiki/Install_instructions]("http://wiki.xmms2.xmms.se/wiki/Install_instructions")

---

### Post by LinuX-M@n1@k on 2008-06-02
I've just installed it, but it still crashes. :(
Here's the new output (again after `xmms2 play`):
```
DEBUG: ../src/xmms/ipc.c:581: Client connected
DEBUG: ../src/xmms/main.c:259: Client xmms2-cli with protocol version 1 sent hello!
DEBUG: ../src/xmms/outputplugin.c:223: Running status changed... 1
DEBUG: ../src/xmms/playlist.c:181: PLAYLIST: updated pos!
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1115: Skipping plugin 'ringbuf'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'replaygain'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'smb'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'm3u'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'cue'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'musepack'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'xspf'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'flac'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'lastfmeta'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'equalizer'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'ofa'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'daap'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'mad'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'gnomevfs'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'curl'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'vorbis'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'mms'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'mp4'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'avcodec'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'modplug'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'xml'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'asx'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'icymetaint'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'wave'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'nulstripper'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'rss'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'sid'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'id3v2'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'file'
DEBUG: ../src/xmms/xform.c:1121: Plugin 'file' matched
DEBUG: ../src/plugins/file/file.c:113: Opening /home/boris/dcpp/02-britney_spears-piece_of_me.mp3
DEBUG: ../src/xmms/xform.c:481: Setting 'size' to 5151668
DEBUG: ../src/xmms/xform.c:481: Setting 'lmod' to 1209292654
DEBUG: ../src/xmms/xform.c:1182: Not in one of 112 goal-types
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1121: Plugin 'magic' matched
DEBUG: ../src/xmms/magic.c:460: magic plugin detected 'application/id3v2' (id3 header)
DEBUG: ../src/xmms/xform.c:1182: Not in one of 112 goal-types
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1115: Skipping plugin 'ringbuf'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'replaygain'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'smb'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'm3u'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'cue'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'musepack'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'xspf'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'flac'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'lastfmeta'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'equalizer'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'ofa'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'daap'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'mad'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'gnomevfs'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'curl'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'vorbis'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'mms'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'mp4'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'avcodec'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'modplug'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'xml'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'asx'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'icymetaint'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'wave'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'nulstripper'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'rss'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'sid'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'id3v2'
DEBUG: ../src/xmms/xform.c:1121: Plugin 'id3v2' matched
DEBUG: ../src/plugins/id3v2/id3.c:508: Found id3v2 header (version=3, rev=0, len=2326, flags=0)
DEBUG: ../src/xmms/xform.c:481: Setting 'size' to 5149342
DEBUG: ../src/plugins/id3v2/id3.c:455: Unhandled tag TLAN
DEBUG: ../src/xmms/xform.c:481: Setting 'tracknr' to 2
DEBUG: ../src/plugins/id3v2/id3.c:455: Unhandled tag TDAT
DEBUG: ../src/plugins/id3v2/id3.c:455: Unhandled tag TSSE
DEBUG: ../src/plugins/id3v2/id3.c:455: Unhandled tag TPUB
DEBUG: ../src/xmms/xform.c:1182: Not in one of 112 goal-types
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1121: Plugin 'magic' matched
DEBUG: ../src/xmms/magic.c:460: magic plugin detected 'audio/mpeg' (mpeg header)
DEBUG: ../src/xmms/xform.c:1182: Not in one of 112 goal-types
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'converter'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'magic'
DEBUG: ../src/xmms/xform.c:1115: Skipping plugin 'ringbuf'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'replaygain'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'smb'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'm3u'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'cue'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'musepack'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'xspf'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'flac'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'lastfmeta'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'equalizer'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'ofa'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'daap'
DEBUG: ../src/xmms/xform.c:1119: Trying plugin 'mad'
DEBUG: ../src/xmms/xform.c:1121: Plugin 'mad' matched
DEBUG: ../src/plugins/mad/xing.c:112: LAME tag found!
DEBUG: ../src/plugins/mad/mad.c:270: File with Xing header!
DEBUG: ../src/xmms/xform.c:481: Setting 'isvbr' to 1
DEBUG: ../src/plugins/mad/mad.c:282: XING duration 212166
DEBUG: ../src/xmms/xform.c:481: Setting 'duration' to 212166
DEBUG: ../src/plugins/mad/mad.c:292: XING bitrate 194157
DEBUG: ../src/xmms/xform.c:481: Setting 'bitrate' to 194157
DEBUG: ../src/plugins/mad/mad.c:304: Samples to skip in the beginning: 576, total: 9353904
DEBUG: ../src/plugins/mad/id3v1.c:134: Found ID3v1 TAG!
DEBUG: ../src/xmms/xform.c:481: Setting 'samplerate' to 44100
DEBUG: ../src/xmms/xform.c:481: Setting 'channels' to 2
DEBUG: ../src/xmms/xform.c:572: Collecting metadata from file
DEBUG: ../src/xmms/xform.c:572: Collecting metadata from magic
DEBUG: ../src/xmms/xform.c:572: Collecting metadata from id3v2
DEBUG: ../src/xmms/xform.c:572: Collecting metadata from magic
DEBUG: ../src/xmms/xform.c:572: Collecting metadata from mad
DEBUG: ../src/plugins/alsa/alsa.c:345: Opening device: default
DEBUG: ../src/xmms/ipc.c:392: disconnect was true!
DEBUG: ../src/xmms/ipc.c:495: Destroying client!
 INFO: ../src/xmms/xform.c:1295: Successfully setup chain for 'file:///home/boris/dcpp/02-britney_spears-piece_of_me.mp3' (27) containing file:magic:id3v2:magic:mad
DEBUG: ../src/xmms/output.c:294: Running hotspot! Song changed!! 27
DEBUG: ../src/xmms/output.c:1007: Setting format!
DEBUG: ../src/plugins/alsa/alsa.c:469: Buffer time requested: 500ms, got: 341ms
Segmentation fault
```
Other ideas ?

***Edit:*** Next time I'll post only the last 8-10 lines...

---

### Post by xc3RnbFO8P on 2008-06-02
Did you do this **./waf build**

---

### Post by LinuX-M@n1@k on 2008-06-02
Yes, when I built it from source.
But I removed it this morning and installed the one from the repos to try it again.

***Edit:*** Sorry for the late reply. I was busy...
***Edit2:*** Oh, and thank you for helping me! ;)

---

### Post by xc3RnbFO8P on 2008-06-02
Do you have **libmad0** and **libmad0-dev** installed?
Check if have mad.h in your file system(Places> Searching for Files)

---

### Post by LinuX-M@n1@k on 2008-06-02
> **Ringi said:**
> Do you have **libmad0** and **libmad0-dev** installed?
Check if have mad.h in your file system(Places> Searching for Files)

Yes, I have them both installed.
```
$ sudo apt-get install libmad0 libmad0-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmad0 is already the newest version.
libmad0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ 
```
And mad.h:
```
$ whereis mad.h
mad: /usr/include/mad.h
$
```
Again, sorry for the late reply.

---

### Post by xc3RnbFO8P on 2008-06-02
Try this (if you haven't):
[http://wiki.xmms2.xmms.se/wiki/FAQ#Why_rewrite_XMMS.3F]("http://wiki.xmms2.xmms.se/wiki/FAQ#Why_rewrite_XMMS.3F")

---

### Post by LinuX-M@n1@k on 2008-06-02
Thanks for the link. However, I couldn't find anything that helped me there :(.

I'll try to start xmms2 in the CLI without X to be sure that none of my apps is blocking the sound card.
*(edit: still crashes)*

And I'll try *.mp3, *.m3u, *.wav and *.wma files.
*(edit: crashes with all of those, except the *.wav ones - xmms2 just doesn't support them and does nothing)*

So, here we go again... What are we going to try next? :)
Thank you for your help!

---

### Post by xc3RnbFO8P on 2008-06-03
Start like this:
> xmms2 radd dcpp
xmms2 play

Not working:
> killall xmms2d
delete /tmp/**[COLOR="Red"]xmms-ipc-boris[/COLOR]**
xmms2 play


---

### Post by LinuX-M@n1@k on 2008-06-04
Thanks for the reply.
Still crashes :(. Here's the output:
```
$ xmms2 radd dcpp
Log output will be stored in /home/boris/.cache/xmms2/xmms2d.log
xmms2 started
$ xmms2 list
->[0/1] mind.in.a.box - Lament for Lost Dreams (snippet) (00:26)
  [1/3] Britney Spears - Piece Of Me (03:32)
  [2/4] Benny Benassi - Love Is Gonna Save Us (05:09)
  [3/2] Black+Eyed+Peas+feat.+Justin+Timberlake+-+Where+Is+The+Love.mp3 (00:00)
  [4/5] Eminem - Mockingbird (04:11)
  [5/6] Foreigner+-+I+Want+To+Know+What+Love+Is.wav (04:47)
  [6/7] Ice Cube - Right Here, Right Now (04:13)
  [7/8] Metallica - Nothing Else Matters (live) (06:22)

Total playtime: 0:28:40
$ xmms2 play
ERROR: Couldn't start playback: Disconnected
$
```
It seems to crash after a few commands:
```
$ **xmms2 list**
[I]Log output will be stored in /home/boris/.cache/xmms2/xmms2d.log
xmms2 started[/I]
->[0/1] mind.in.a.box - Lament for Lost Dreams (snippet) (00:26)

Total playtime: 0:00:26
$ **xmms2 list**
->[0/1] mind.in.a.box - Lament for Lost Dreams (snippet) (00:26)

Total playtime: 0:00:26
$ **xmms2 list**
*ERROR: Disconnected*
$ 
```
:confused:

---

### Post by LinuX-M@n1@k on 2008-06-04
I've just tried something:

I ran `xmms2d -v`.
I looked for 'xmms2' in the processes list (or whatever it is):
```
$ ps ax |grep xmms2
 7227 pts/2    Sl+    0:00 xmms2d -v
** 7238 pts/2    S+     0:00 /usr/bin/xmms2-mlib-updater**
 7240 pts/2    S+     0:00 /usr/bin/xmms2-et
 7244 pts/1    R+     0:00 grep xmms2
$
```
Then I ran `xmms2 play` and the output from xmms2d was:
```
...
DEBUG: ../src/xmms/output.c:273: Running hotspot! Song changed!! 1
DEBUG: ../src/xmms/output.c:988: Setting format!
DEBUG: ../src/plugins/alsa/alsa.c:461: Buffer time requested: 500ms, got: 341ms

** (**process:7238**): WARNING **: xmms2d disconnected us
Segmentation fault
$ 
```
I hope this helps :/

---

### Post by xc3RnbFO8P on 2008-06-04
Look at this:
[http://bugs.xmms2.xmms.se/my_view_page.php]("http://bugs.xmms2.xmms.se/my_view_page.php")

---

### Post by LinuX-M@n1@k on 2008-06-06
> **Ringi said:**
> Look at this:
[http://bugs.xmms2.xmms.se/my_view_page.php]("http://bugs.xmms2.xmms.se/my_view_page.php")

Thanks for the link. Finally it's fixed!

I downloaded it from git and compiled it. Now it works like a charm ;)!
```
git clone git://git.debian.org/git/pkg-xmms2/xmms2.git
cd xmms2
./waf configure && ./waf build && sudo ./waf install
```

Now it's left to set up the equalizer to the 'Full Bass & Treble' preset, and I have no idea how to do it.

---

