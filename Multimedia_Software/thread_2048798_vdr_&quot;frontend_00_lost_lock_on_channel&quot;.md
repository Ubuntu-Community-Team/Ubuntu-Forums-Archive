---
title: "vdr &quot;frontend 0/0 lost lock on channel&quot;"
date: 2012-08-27
forum: Multimedia Software
---

### Post by lvancleef on 2012-08-27
Hi ubuntuforums,

I am struggling with vdr 1.7.22 using a WinTV-HVR1100 on Kubuntu 12.04, 64 bit. 

```
$ uname -a
Linux laplace 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```Problem: When vdr is started on boot using /etc/init.d/vdr (runlevel 2) it reports an error:

```
$ grep vdr /var/log/syslog
[...]
Aug 27 13:16:56 laplace vdr: [1583] frontend 0/0 lost lock on channel 1, tp 602
Aug 27 13:16:58 laplace vdr: [1583] frontend 0/0 timed out while tuning to channel 1, tp 602
```This error can be solved by a restart of vdr:

```
$ sudo service vdr restart
```Also, it does _NOT_ happen when vdr is not started on boot but once the system is running and vdr started with:

```
$ sudo service vdr start
```Anybody any ideas what is happening?

Thank you in advance, cheers!

------- Full syslog of a failed vdr start:

```
Aug 27 13:16:47 laplace vdr: [1370] VDR version 1.7.22 started
Aug 27 13:16:47 laplace vdr: [1370] switched to user 'vdr'
Aug 27 13:16:47 laplace vdr: [1370] codeset is 'UTF-8' - known
Aug 27 13:16:47 laplace vdr: [1370] found 28 locales in /usr/share/locale
Aug 27 13:16:47 laplace vdr: [1370] loading plugin: /usr/lib/vdr/plugins/libvdr-xineliboutput.so.1.7.22
Aug 27 13:16:47 laplace vdr: [1370] [xine..put] Listening on address '0.0.0.0' port 37890
Aug 27 13:16:47 laplace vdr: [1370] loading plugin: /usr/lib/vdr/plugins/libvdr-skinenigmang.so.1.7.22
Aug 27 13:16:47 laplace vdr: [1370] loading plugin: /usr/lib/vdr/plugins/libvdr-remote.so.1.7.22
Aug 27 13:16:47 laplace vdr: [1370] loading plugin: /usr/lib/vdr/plugins/libvdr-femon.so.1.7.22
Aug 27 13:16:47 laplace vdr: [1370] loading /var/lib/vdr/setup.conf
Aug 27 13:16:47 laplace vdr: [1370] ERROR: unknown config parameter: RecordDolbyDigital = 1
Aug 27 13:16:47 laplace vdr: [1370] [xine..put] Skipping configuration entry Remote.ListenPort=37890 (overridden in command line)
Aug 27 13:16:47 laplace vdr: [1370] [xine..put] Skipping configuration entry Remote.LocalIP=127.0.0.1 (overridden in command line)
Aug 27 13:16:47 laplace vdr: [1370] [xine..put] Skipping configuration entry RemoteMode=1 (overridden in command line)
Aug 27 13:16:47 laplace vdr: [1370] loading /var/lib/vdr/sources.conf
Aug 27 13:16:47 laplace vdr: [1370] loading /var/lib/vdr/diseqc.conf
Aug 27 13:16:47 laplace vdr: [1370] loading /var/lib/vdr/channels.conf
Aug 27 13:16:47 laplace vdr: [1370] loading /var/lib/vdr/timers.conf
Aug 27 13:16:47 laplace vdr: [1370] loading /var/lib/vdr/commands.conf
Aug 27 13:16:47 laplace vdr: [1370] loading /var/lib/vdr/reccmds.conf
Aug 27 13:16:47 laplace vdr: [1370] loading /var/lib/vdr/svdrphosts.conf
Aug 27 13:16:47 laplace vdr: [1370] loading /var/lib/vdr/remote.conf
Aug 27 13:16:47 laplace vdr: [1370] loading /var/lib/vdr/keymacros.conf
Aug 27 13:16:48 laplace vdr: [1370] reading EPG data from /var/cache/vdr/epg.data
Aug 27 13:16:48 laplace vdr: [1581] video directory scanner thread started (pid=1370, tid=1581)
Aug 27 13:16:48 laplace vdr: [1580] video directory scanner thread started (pid=1370, tid=1580)
Aug 27 13:16:48 laplace vdr: [1370] registered source parameters for 'A - ATSC'
Aug 27 13:16:48 laplace vdr: [1370] registered source parameters for 'C - DVB-C'
Aug 27 13:16:48 laplace vdr: [1370] registered source parameters for 'S - DVB-S'
Aug 27 13:16:48 laplace vdr: [1370] registered source parameters for 'T - DVB-T'
Aug 27 13:16:48 laplace vdr: [1370] probing /dev/dvb/adapter0/frontend0
Aug 27 13:16:48 laplace vdr: [1370] creating cDvbDevice
Aug 27 13:16:48 laplace vdr: [1370] new device number 1
Aug 27 13:16:48 laplace vdr: [1370] frontend 0/0 provides DVB-T with QPSK,QAM16,QAM64 ("Conexant CX22702 DVB-T")
Aug 27 13:16:48 laplace vdr: [1370] found 1 DVB device
Aug 27 13:16:48 laplace vdr: [1583] tuner on frontend 0/0 thread started (pid=1370, tid=1583)
Aug 27 13:16:48 laplace vdr: [1583] cTimeMs: using monotonic clock (resolution is 1 ns)
Aug 27 13:16:48 laplace vdr: [1584] section handler thread started (pid=1370, tid=1584)
Aug 27 13:16:48 laplace vdr: [1370] initializing plugin: xineliboutput (1.0.90-cvs): X11/xine-lib Ausgabe-Plugin
Aug 27 13:16:48 laplace vdr: [1370] new device number 9
Aug 27 13:16:48 laplace vdr: [1370] [xine..put] cTimePts: clock_gettime(CLOCK_MONOTONIC): clock resolution 0 us
Aug 27 13:16:48 laplace vdr: [1370] [xine..put] cTimePts: using monotonic clock
Aug 27 13:16:48 laplace vdr: [1370] [xine..put] RTP SSRC: 0x301f20f7
Aug 27 13:16:48 laplace vdr: [1370] initializing plugin: skinenigmang (0.1.1): EnigmaNG Oberfläche
Aug 27 13:16:48 laplace vdr: [1370] initializing plugin: remote (0.4.0): Fernbedienung
Aug 27 13:16:48 laplace vdr: [1370] initializing plugin: femon (1.7.11): DVB Signal Informationsanzeige (OSD)
Aug 27 13:16:48 laplace vdr: [1370] setting primary device to 2
Aug 27 13:16:48 laplace vdr: [1370] assuming manual start of VDR
Aug 27 13:16:48 laplace vdr: [1370] SVDRP listening on port 6419
Aug 27 13:16:48 laplace vdr: [1370] skin "EnigmaNG" not available - using "classic" instead
Aug 27 13:16:48 laplace vdr: [1370] loading /var/lib/vdr/themes/classic-default.theme
Aug 27 13:16:48 laplace vdr: [1370] starting plugin: xineliboutput
Aug 27 13:16:48 laplace vdr: [1586] Remote decoder/display server (cXinelibServer) thread started (pid=1370, tid=1586)
Aug 27 13:16:48 laplace vdr: [1586] [xine..put] cXinelibServer priority set successful SCHED_RR 2 [1,99]
Aug 27 13:16:48 laplace vdr: [1586] [xine..put] Binding server to 0.0.0.0:37890
Aug 27 13:16:48 laplace vdr: [1586] [xine..put] Listening on port 37890
Aug 27 13:16:48 laplace vdr: [1586] [discovery] UDP broadcast send failed (discovery)
Aug 27 13:16:48 laplace vdr: [1586] [discovery]    (ERROR (tools/vdrdiscovery.c,97): Das Netzwerk ist nicht erreichbar)
Aug 27 13:16:48 laplace vdr: [1370] [xine..put] cXinelibDevice::StartDevice(): Device started
Aug 27 13:16:48 laplace vdr: [1370] starting plugin: skinenigmang
Aug 27 13:16:48 laplace vdr: [1370] starting plugin: remote
Aug 27 13:16:48 laplace vdr: [1370] device /dev/input/event0: Power Button
Aug 27 13:16:48 laplace vdr: [1370] device /dev/input/event1: Power Button
Aug 27 13:16:48 laplace vdr: [1370] device /dev/input/event2: AT Translated Set 2 keyboard
Aug 27 13:16:48 laplace vdr: [1370] device /dev/input/event3: Logitech USB Mouse
Aug 27 13:16:48 laplace vdr: [1370] device /dev/input/event4: cx88 IR (Hauppauge WinTV-HVR110
Aug 27 13:16:48 laplace vdr: [1370] device /dev/input/event5: MCE IR Keyboard/Mouse (cx88xx)
Aug 27 13:16:48 laplace vdr: [1370] remote: using '/dev/input/ir'
Aug 27 13:16:48 laplace vdr: [1370] remote-ir: autorepeat supported
Aug 27 13:16:48 laplace vdr: [1370] remote-ir: exclusive access granted
Aug 27 13:16:48 laplace vdr: [1370] starting plugin: femon
Aug 27 13:16:48 laplace vdr: [1370] setting current skin to "EnigmaNG"
Aug 27 13:16:48 laplace vdr: [1370] loading /var/lib/vdr/themes/EnigmaNG-default.theme
Aug 27 13:16:48 laplace vdr: [1370] ERROR (lirc.c,48): /var/run/lirc/lircd: Datei oder Verzeichnis nicht gefunden
Aug 27 13:16:48 laplace vdr: [1370] remote control remote-ir - keys known
Aug 27 13:16:48 laplace vdr: [1370] ERROR: remote control LIRC not ready!
Aug 27 13:16:48 laplace vdr: [1370] switching to channel 1
Aug 27 13:16:48 laplace vdr: [1600] receiver on device 1 thread started (pid=1370, tid=1600)
Aug 27 13:16:48 laplace vdr: [1601] TS buffer on device 1 thread started (pid=1370, tid=1601)
Aug 27 13:16:48 laplace vdr: [1370] OSD size changed to 720x576 @ 1.42222
Aug 27 13:16:48 laplace vdr: [1370] EnigmaNG: cPluginSkinEnigma::LoadChannelLogo: LOGO "Das Erste.xpm" NOT FOUND in /usr/share/vdr-enigmang-icons/[hq]logos
Aug 27 13:16:48 laplace vdr: [1370] EnigmaNG: cPluginSkinEnigma::LoadXpm(/usr/share/vdr-enigmang-icons/hqlogos/no_logo.xpm) LOGO NOT FOUND
Aug 27 13:16:49 laplace vdr: [1581] video directory scanner thread ended (pid=1370, tid=1581)
Aug 27 13:16:49 laplace vdr: [1600] [xine..put] Detected video size 704x576
Aug 27 13:16:49 laplace vdr: [1580] video directory scanner thread ended (pid=1370, tid=1580)
Aug 27 13:16:56 laplace vdr: [1583] frontend 0/0 lost lock on channel 1, tp 602
Aug 27 13:16:58 laplace vdr: [1583] frontend 0/0 timed out while tuning to channel 1, tp 602
Aug 27 13:18:01 laplace vdr: [1583] frontend 0/0 timed out while tuning to channel 1, tp 602
Aug 27 13:19:04 laplace vdr: [1583] frontend 0/0 timed out while tuning to channel 1, tp 602
```

---

### Post by lvancleef on 2012-08-29
Please find two more logs attached:

1) kernel log
2) vdr log

=> For me, it looks like all the modules are loaded before vdr starts, right?

---

