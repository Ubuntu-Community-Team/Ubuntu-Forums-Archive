---
title: "use smartmouse phoenix"
date: 2010-05-01
forum: Multimedia Software
---

### Post by Saiph on 2010-05-01
I use Ubuntu Lucid.
I've got smartmouse phoenix and I would like to used it over COM1 port(I've got only one com) with my skylink card.

dmesg | grep ttyS
[    0.464730] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.465039] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

Serial Port is recognized by my system.

Is here detecting my Smartmouse-Phoenix?
[   10.329942] snd-ca0106: Model 1012 Rev 00000000 Serial 10121102
[   10.366073] usbcore: registered new interface driver usbserial
[   10.366502] USB Serial support registered for generic
[   10.366930] usbcore: registered new interface driver usbserial_generic
[   10.366933] usbserial: USB Serial Driver core
[   10.383966] Console: switching to colour frame buffer device 80x30
[   10.391101] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.403983] DVB: registering new adapter (bttv0)
[   10.412798] USB Serial support registered for FTDI USB Serial Device
[   10.413366] usbcore: registered new interface driver ftdi_sio
[   10.413368] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver


**[SIZE="6"]How can I use it? [/SIZE]**


/dev/ttyS0 used in plugin-sc.conf
Vdr 1.7.10 with sc: restart  :
May  1 17:39:55 lucid vdr: [8325] stopping plugin: streamdev-server
May  1 17:39:55 lucid vdr: [8333] streamdev server thread ended (pid=8325, tid=8333)
May  1 17:39:55 lucid vdr: [8325] stopping plugin: sc
May  1 17:39:56 lucid vdr: [8332] SC housekeeper thread ended (pid=8325, tid=8332)
May  1 17:39:56 lucid vdr: [8331] SC-CI adapter on device 0 thread ended (pid=8325, tid=8331)
May  1 17:39:56 lucid vdr: [8339] logger stats thread ended (pid=8325, tid=8339)
May  1 17:39:56 lucid vdr: [8325] [general.debug] SC cleanup done
May  1 17:39:56 lucid vdr: [8325] saved setup to /var/lib/vdr/setup.conf
May  1 17:39:56 lucid vdr: [8330] section handler thread ended (pid=8325, tid=8330)
May  1 17:39:56 lucid vdr: [8329] tuner on device 1 thread ended (pid=8325, tid=8329)
May  1 17:39:56 lucid vdr: [8325] deleting plugin: streamdev-server
May  1 17:39:56 lucid vdr: [8325] deleting plugin: sc
May  1 17:39:56 lucid vdr: [8325] =====================
May  1 17:39:56 lucid vdr: [8325] EPG bugfix statistics
May  1 17:39:56 lucid vdr: [8325] =====================
May  1 17:39:56 lucid vdr: [8325] IF SOMEBODY WHO IS IN CHARGE OF THE EPG DATA FOR ONE OF THE LISTED
May  1 17:39:56 lucid vdr: [8325] CHANNELS READS THIS: PLEASE TAKE A LOOK AT THE FUNCTION cEvent::FixEpgBugs()
May  1 17:39:56 lucid vdr: [8325] IN VDR/epg.c TO LEARN WHAT'S WRONG WITH YOUR DATA, AND FIX IT!
May  1 17:39:56 lucid vdr: [8325] =====================
May  1 17:39:56 lucid vdr: [8325] Fix#011Hits#011Channels
May  1 17:39:56 lucid vdr: [8325] 6#011912#011Animal Planet, Hallmark CE, Viasat History, Duna TV, ATV, Pro Cinema, Film +, ...
May  1 17:39:56 lucid vdr: [8325] 7#0111351#011STV 2, STV 1, HBO Comedy Adria, TVR2, NOVA TV, HBO Adria, Reality TV, Duna TV, ...
May  1 17:39:56 lucid vdr: [8325] 12#011798#011STV 2, STV 1, HBO Comedy Adria, NOVA TV, HBO Adria, Markiza, Joj, ATV, AXN, ...
May  1 17:39:56 lucid vdr: [8325] =====================
May  1 17:39:56 lucid vdr: [8325] max. latency time 2 seconds
May  1 17:39:56 lucid vdr: [8325] caught signal 15
May  1 17:39:56 lucid vdr: [8325] exiting, exit code 0
May  1 17:40:00 lucid vdr: [8454] cTimeMs: using monotonic clock (resolution is 1 ns)
May  1 17:40:00 lucid vdr: [8470] cTimeMs: using monotonic clock (resolution is 1 ns)
May  1 17:40:00 lucid vdr: [8473] cTimeMs: using monotonic clock (resolution is 1 ns)
May  1 17:40:00 lucid vdr: [8513] cTimeMs: using monotonic clock (resolution is 1 ns)
May  1 17:40:00 lucid vdr: [8513] VDR version 1.7.10 started
May  1 17:40:00 lucid vdr: [8513] switched to user 'vdr'
May  1 17:40:00 lucid vdr: [8513] codeset is 'UTF-8' - known
May  1 17:40:00 lucid vdr: [8513] found 25 locales in /usr/share/locale
May  1 17:40:00 lucid vdr: [8513] loading plugin: /usr/lib/vdr/plugins/libvdr-sc.so.1.7.10
May  1 17:40:00 lucid vdr: [8513] loading plugin: /usr/lib/vdr/plugins/libvdr-streamdev-server.so.1.7.10
May  1 17:40:00 lucid vdr: [8513] loading /var/lib/vdr/setup.conf
May  1 17:40:00 lucid vdr: [8513] loading /var/lib/vdr/sources.conf
May  1 17:40:00 lucid vdr: [8513] loading /var/lib/vdr/diseqc.conf
May  1 17:40:00 lucid vdr: [8513] loading /var/lib/vdr/channels.conf
May  1 17:40:00 lucid vdr: [8513] loading /var/lib/vdr/timers.conf
May  1 17:40:00 lucid vdr: [8513] Failed to load translated '/var/lib/vdr/commands.conf.' for language ()
May  1 17:40:00 lucid vdr: [8513] Falling back to default '/var/lib/vdr/commands.conf' (if any)
May  1 17:40:00 lucid vdr: [8513] loading /var/lib/vdr/commands.conf
May  1 17:40:00 lucid vdr: [8513] Failed to load translated '/var/lib/vdr/reccmds.conf.' for language ()
May  1 17:40:00 lucid vdr: [8513] Falling back to default '/var/lib/vdr/reccmds.conf' (if any)
May  1 17:40:00 lucid vdr: [8513] loading /var/lib/vdr/reccmds.conf
May  1 17:40:00 lucid vdr: [8513] Failed to load translated '/var/lib/vdr/timercmds.conf.' for language ()
May  1 17:40:00 lucid vdr: [8513] Falling back to default '/var/lib/vdr/timercmds.conf' (if any)
May  1 17:40:00 lucid vdr: [8513] loading /var/lib/vdr/svdrphosts.conf
May  1 17:40:00 lucid vdr: [8513] loading /var/lib/vdr/keymacros.conf
May  1 17:40:00 lucid vdr: [8514] video directory scanner thread started (pid=8513, tid=8514)
May  1 17:40:00 lucid vdr: [8513] reading EPG data from /var/cache/vdr/epg.data
May  1 17:40:00 lucid vdr: [8515] video directory scanner thread started (pid=8513, tid=8515)
May  1 17:40:00 lucid vdr: [8515] video directory scanner thread ended (pid=8513, tid=8515)
May  1 17:40:00 lucid vdr: [8514] video directory scanner thread ended (pid=8513, tid=8514)
May  1 17:40:00 lucid vdr: [8513] no DVB device found
May  1 17:40:00 lucid vdr: [8513] initializing plugin: sc (1.0.0pre-HG-28d5438fad67+): A software emulated CAM
May  1 17:40:00 lucid vdr: [8513] [general.info] SC version 1.0.0pre-HG-28d5438fad67+ initializing (VDR 1.7.10)
May  1 17:40:00 lucid vdr: [8513] [general.debug] probing /dev/dvb/adapter0/frontend0
May  1 17:40:00 lucid vdr: [8513] [general.debug] capturing device 0
May  1 17:40:00 lucid vdr: [8513] device 1 provides DVB-S ("DST DVB-S")
May  1 17:40:00 lucid vdr: [8517] tuner on device 1 thread started (pid=8513, tid=8517)
May  1 17:40:00 lucid vdr: [8518] section handler thread started (pid=8513, tid=8518)
May  1 17:40:00 lucid vdr: [8513] [general.info] captured 1 video device
May  1 17:40:00 lucid vdr: [8513] initializing plugin: streamdev-server (0.5.0-pre): VDR prúdový server
May  1 17:40:00 lucid vdr: [8513] setting primary device to 1
May  1 17:40:00 lucid vdr: [8513] device 1 has no MPEG decoder
May  1 17:40:00 lucid vdr: [8513] assuming manual start of VDR
May  1 17:40:00 lucid vdr: [8513] SVDRP listening on port 2001
May  1 17:40:00 lucid vdr: [8513] setting current skin to "sttng"
May  1 17:40:00 lucid vdr: [8513] loading /var/lib/vdr/themes/sttng-default.theme
May  1 17:40:00 lucid vdr: [8513] starting plugin: sc
May  1 17:40:00 lucid vdr: [8513] [general.info] SC version 1.0.0pre-HG-28d5438fad67+ starting (VDR 1.7.10)
May  1 17:40:00 lucid vdr: [8513] [general.info] loading cardclient config from /var/lib/vdr/plugins/sc/cardclient.conf
May  1 17:40:00 lucid vdr: [8513] [general.warn] no write permission on /var/lib/vdr/plugins/sc/cardclient.conf. Changes will not be saved!
May  1 17:40:00 lucid vdr: [8513] [general.info] loading keys from /var/lib/vdr/plugins/sc/SoftCam.Key
May  1 17:40:00 lucid vdr: [8513] [general.info] loading ecm cache from /var/lib/vdr/plugins/sc/ecm.cache
May  1 17:40:00 lucid vdr: [8513] [general.error] failed open /var/lib/vdr/plugins/sc/smartcard.conf: No such file or directory
May  1 17:40:00 lucid vdr: [8513] [general.error] failed open /var/lib/vdr/plugins/sc/cardslot.conf: No such file or directory
May  1 17:40:00 lucid vdr: [8513] [general.error] failed open /var/lib/vdr/plugins/sc/override.conf: No such file or directory
May  1 17:40:00 lucid vdr: [8513] [general.info] Using software decryption on card 0
May  1 17:40:00 lucid vdr: [8519] SC-CI adapter on device 0 thread started (pid=8513, tid=8519)
May  1 17:40:00 lucid vdr: [8513] starting plugin: streamdev-server
May  1 17:40:00 lucid vdr: [8513] loading /var/lib/vdr/plugins/streamdev/streamdevhosts.conf
May  1 17:40:00 lucid vdr: [8521] streamdev server thread started (pid=8513, tid=8521)
May  1 17:40:00 lucid vdr: [8513] ERROR: /dev/lircd: No such file or directory
May  1 17:40:00 lucid vdr: [8513] ERROR: remote control LIRC not ready!
May  1 17:40:00 lucid vdr: [8520] SC housekeeper thread started (pid=8513, tid=8520)
May  1 17:40:00 lucid vdr: [8521] Streamdev: Listening (VTP) on port 2004
May  1 17:40:00 lucid vdr: [8521] Streamdev: Listening (HTTP) on port 3000
May  1 17:40:02 lucid vdr: [8519] CAM 1: module ready
May  1 17:40:03 lucid vdr: [8519] CAM 1: replies to QUERY - multi channel decryption possible
May  1 17:40:03 lucid vdr: [8513] switching to channel 1
May  1 17:40:03 lucid vdr: [8513] CAM 1: assigned to device 1
May  1 17:40:03 lucid vdr: [8523] ecmhandler 0 filter thread started (pid=8513, tid=8523)
May  1 17:40:03 lucid vdr: [8524] receiver on device 1 thread started (pid=8513, tid=8524)
May  1 17:40:03 lucid vdr: [8513] setting watchdog timer to 60 seconds
May  1 17:40:03 lucid vdr: [8513] ERROR: Kanál je zamknutý (nahráva sa)!
May  1 17:40:03 lucid vdr: [8525] TS buffer on device 1 thread started (pid=8513, tid=8525)
May  1 17:40:03 lucid vdr: [8513] ERROR: no OSD provider available - using dummy OSD!
May  1 17:40:03 lucid vdr: [8526] logger stats thread started (pid=8513, tid=8526)
May  1 17:40:03 lucid vdr: [8527] logger 0 filter thread started (pid=8513, tid=8527)
May  1 17:40:05 lucid vdr: [8513] OSD size changed to 720x480 @ 1
May  1 17:40:05 lucid vdr: [8513] max. latency time 2 seconds
May  1 17:40:05 lucid vdr: [8513] retuning due to modification of channel 1
May  1 17:40:05 lucid vdr: [8513] switching to channel 1
May  1 17:40:05 lucid vdr: [8525] TS buffer on device 1 thread ended (pid=8513, tid=8525)
May  1 17:40:05 lucid vdr: [8524] buffer stats: 39856 (0%) used
May  1 17:40:05 lucid vdr: [8524] receiver on device 1 thread ended (pid=8513, tid=8524)
May  1 17:40:05 lucid vdr: [8528] receiver on device 1 thread started (pid=8513, tid=8528)



Thank you.

---

