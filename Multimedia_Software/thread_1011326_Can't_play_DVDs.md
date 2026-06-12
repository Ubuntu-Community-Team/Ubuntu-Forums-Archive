---
title: "Can't play DVDs"
date: 2008-12-14
forum: Multimedia Software
---

### Post by bayesian on 2008-12-14
Have been reading here and have done most things that people are saying to do to get DVDs playing in ubuntu. 

Here is the output of the error in VLC:

[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/iain/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
[00000376] dvdnav demux error: cannot set title (can't decrypt DVD?)
libdvdread: Invalid title IFO (VTS_01_0.IFO).
[00000376] dvdread demux error: read failed for block 0
^C[00000373] signals interface error: Caught Interrupt signal, exiting...

And the error with Totem:
** (totem:12827): DEBUG: Init of Python module
** (totem:12827): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:12827): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:12827): DEBUG: Creating Python plugin instance
** (totem:12827): DEBUG: Init of Python module
** (totem:12827): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:12827): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:12827): DEBUG: Creating Python plugin instance
libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Invalid title IFO (VTS_01_0.IFO).
** Message: no file info
** Message: no file info
** Message: no file info
Device is now /dev/scd0
libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: AVP2_REQUIEM_EXTENDED
libdvdnav: DVD Serial Number: 38751494
libdvdnav: DVD Title (Alternative): SE_F1_D1
libdvdnav: Unable to find map file '/home/iain/.dvdnav/AVP2_REQUIEM_EXTENDED.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
VTS change
cur audio stream change
NAV packet discont: cur_end_ts 99:99:99.999999999 !=  vobu_start_ptm: 0:00:00.336711111 base 0:00:00.000000000
seek completed. New start TS 0:00:00.336711111 pos 0:00:00.000000000
Pushing stream event
Pushing clut event
Pushing spu_select event
Pushing audio_select event
Discont packet
Pushing highlight event with TS 99:99:99.999999999
demux: got segment update 0 start 336711111 stop -1 time 0
sending new segment: update 0 rate 1 format 3, start: 10000000000, stop: -1, time: 0 scr_adjust: 869696(0:00:09.663288888)
****** FIXME: WAIT *****
**** STILL FRAME. Duration 1 ****
**** AUDIO MUNGE: still-state now 1
demux: got segment update 1 start 336711111 stop 1336711111 time 0
sending new segment: update 1 rate 1 format 3, start: 10000000000, stop: 11000000000, time: 0 scr_adjust: 869696(0:00:09.663288888)
***********  Sending audio fill: accum = 0:00:00.000000000 still-state=1
Sending 38400 bytes (0:00:00.100000000) of audio data with TS 0:00:10.000000000

(totem:12827): GLib-GObject-WARNING **: IA__g_object_get_valist: object class `GstPlayBin' has no property named `current-subpicture'
**** AUDIO MUNGE: still-state now 0
VTS change
cur audio stream change
NAV packet discont: cur_end_ts 0:00:01.336711111 !=  vobu_start_ptm: 0:00:00.336711111 base 0:00:00.000000000
Pushing stream event
Pushing spu_select event
Pushing audio_select event
seek completed. New start TS 0:00:00.336711111 pos 0:00:00.000000000
demux: got segment update 1 start 336711111 stop 1336711111 time 0
sending new segment: update 1 rate 1 format 3, start: 10000000000, stop: 11000000000, time: 0 scr_adjust: 869696(0:00:09.663288888)
demux: got segment update 0 start 336711111 stop -1 time 0
sending new segment: update 0 rate 1 format 3, start: 11000000000, stop: -1, time: 0 scr_adjust: 959696(0:00:10.663288888)
** Message: Error: Could not read from resource.
resindvdsrc.c(827): rsn_dvdsrc_step (): /GstPlayBin:play/RsnDvdBin:source/resinDvdSrc:dvdsrc:
Failed to read next DVD block. Error: Error reading from DVD.


Anyone able to shed some light on this?

---

### Post by bayesian on 2008-12-14
And now its working perfectly... weird...

---

