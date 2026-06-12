---
title: "MythTV can't find any channels by scanning"
date: 2013-01-14
forum: Multimedia Software
---

### Post by mrchnk on 2013-01-14
I have clean installation of xubuntu 12.04
And MythTV from official repo

```
mrchnk@linuxtv:~$ mythfrontend --version
Please attach all output as a file in bug reports.
MythTV Version : v0.25.2-15-g46cab93
MythTV Branch : fixes/0.25
Network Protocol : 72
Library API : 0.25.20120506-1
QT Version : 4.8.1
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_ceton using_hdpvr using_iptv using_ivtv using_joystick_menu using_libcec using_libcrypto using_libdns_sd using_libxml2 using_lirc using_mheg using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_v4l2 using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_live using_mheg using_libass using_libxml2

```

i have AVerMedia AverTV analogue video capture pci-card installed
```
mrchnk@linuxtv:~$ sudo lspci -vv
...
02:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: Avermedia Technologies Inc AVerTV WDM Video Capture
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (4000ns min, 10000ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f7efe000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
		No end tag found
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: bttv
	Kernel modules: bttv

02:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: Avermedia Technologies Inc AVerTV WDM Audio Capture
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (1000ns min, 63750ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f7eff000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
		No end tag found
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
...
```

and that card works perfectly with some tv software (tvtime, xawtv, scantv)

i choose Analog V4L capture card, try-all channel scan
after the scan it could not find any [new] channels

also i was trying to confugure at least one channel manually (setting up right freq and format) but frontend could not start video stream with following message in console:
```
2013-01-14 14:45:09.600470 I  TV: Creating TV object
2013-01-14 14:45:09.614148 N  Suspending idle timer
2013-01-14 14:45:09.623401 I  TV: Created TvPlayWindow.
2013-01-14 14:45:09.785655 I  TV: Attempting to change from None to WatchingLiveTV
2013-01-14 14:45:09.785725 I  MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
2013-01-14 14:45:09.787477 I  Using protocol version 72
2013-01-14 14:45:09.790801 N  TV: Spawning LiveTV Recorder -- begin
2013-01-14 14:45:09.819920 N  TV: Spawning LiveTV Recorder -- end
2013-01-14 14:45:09.821027 E  GetEntryAt(-1) failed.
2013-01-14 14:45:09.821075 E  It appears that your backend may be misconfigured.  Check your backend logs to determine whether your capture cards, lineups, channels, or storage configuration are reporting errors.  This issue is commonly caused by failing to complete all setup steps properly.  You may wish to review the documentation for mythtv-setup.
2013-01-14 14:45:09.821240 E  EntryToProgram(0@Thu Jan 1 03:00:00 1970) failed to get pginfo
2013-01-14 14:45:09.821271 E  TV: HandleStateChange(): LiveTV not successfully started
2013-01-14 14:45:09.821507 E  TV: LiveTV not successfully started
2013-01-14 14:45:09.878132 I  TV: Main UI disabled.
2013-01-14 14:45:09.879871 I  TV: Entering main playback loop.
2013-01-14 14:45:09.891529 I  TV: Exiting main playback loop.

```

i will appreciate for any advice or help

---

