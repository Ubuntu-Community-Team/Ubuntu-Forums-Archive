---
title: "Ceton Infinitv Pcie VDR or Tvheadend"
date: 2012-05-02
forum: Multimedia Software
---

### Post by speed32219 on 2012-05-02
I have been trying to get the Ceton tuner to work with TVheaend or VDR without any luck.  After installing the Drivers I am able to view channels with sound using the command "cat /dev/ceton/ctn91xx_mpeg0_0 | mplayer -cache 8192 -".
(How would I do this over the network? I can start it on the server using ssh, but server is on other side of house, just to check that the ceton is still working) 

$ls /dev/ct*

/dev/ctn91xx_ctl0	/dev/ctn91xx_filter0_2	/dev/ctn91xx_filter0_5	  
/dev/ctn91xx_filter0_0	/dev/ctn91xx_filter0_3		
/dev/ctn91xx_filter0_1	/dev/ctn91xx_filter0_4
/dev/ctn91xx_mpeg0_0	/dev/ctn91xx_mpeg0_1
/dev/ctn91xx_mpeg0_2    /dev/ctn91xx_mpeg0_3	                                             
/dev/ctn91xx_mpeg0_4    /dev/ctn91xx_mpeg0_5

Since it is not a DVB type device, I have been trying to setup VDR and TVheadend using an IPTV type device.  But the Comcast cable m-card I believe supports Switched Digital Video not IPTV, so I wonder if someone could point me in the right direction.  It's not a dvb type device, so how do I configure it within TBheadend or VDR?  I know MythTV works with Ceton, but wanted something lighter that supports both front-end and back-end on same PC. 

When I try and run streamdev (VDR) from my pc on port 3000 I see the channels I setup for IPTV in the channels.conf, but I get errors in syslog.  I just do not know how to setup the Comcast stream with the ceton tuner and m-card.

Here is the syslog from when I start up VDR:
```
May  2 10:48:31 TV_Server vdr: [4147] VDR version 1.7.21 started
May  2 10:48:31 TV_Server vdr: [4147] switched to user 'vdr'
May  2 10:48:31 TV_Server vdr: [4147] codeset is 'UTF-8' - known
May  2 10:48:31 TV_Server vdr: [4147] found 28 locales in /usr/share/locale
May  2 10:48:31 TV_Server vdr: [4147] loading plugin: /usr/lib/vdr/plugins/libvdr-xineliboutput.so.1.7.21
May  2 10:48:31 TV_Server vdr: [4147] [xine..put] Listening on address '127.0.0.1' port 37890
May  2 10:48:31 TV_Server vdr: [4147] loading plugin: /usr/lib/vdr/plugins/libvdr-streamdev-server.so.1.7.21
May  2 10:48:31 TV_Server vdr: [4147] loading plugin: /usr/lib/vdr/plugins/libvdr-conflictcheckonly.so.1.7.21
May  2 10:48:31 TV_Server vdr: [4147] loading plugin: /usr/lib/vdr/plugins/libvdr-vnsiserver.so.1.7.21
May  2 10:48:31 TV_Server vdr: [4147] loading plugin: /usr/lib/vdr/plugins/libvdr-quickepgsearch.so.1.7.21
May  2 10:48:31 TV_Server vdr: [4147] loading plugin: /usr/lib/vdr/plugins/libvdr-vdrmanager.so.1.7.21
May  2 10:48:31 TV_Server vdr: [4147] forceCheckSvdrp = true 5
May  2 10:48:31 TV_Server vdr: [4147] loading plugin: /usr/lib/vdr/plugins/libvdr-epgsearchonly.so.1.7.21
May  2 10:48:31 TV_Server vdr: [4147] loading plugin: /usr/lib/vdr/plugins/libvdr-epgsearch.so.1.7.21
May  2 10:48:31 TV_Server vdr: [4147] loading plugin: /usr/lib/vdr/plugins/libvdr-eepg.so.1.7.21
May  2 10:48:31 TV_Server vdr: [4147] loading plugin: /usr/lib/vdr/plugins/libvdr-xvdr.so.1.7.21
May  2 10:48:31 TV_Server vdr: [4147] loading plugin: /usr/lib/vdr/plugins/libvdr-iptv.so.1.7.21
May  2 10:48:31 TV_Server vdr: [4147] loading /var/lib/vdr/setup.conf
May  2 10:48:31 TV_Server vdr: [4147] loading /var/lib/vdr/sources.conf
May  2 10:48:31 TV_Server vdr: [4147] loading /var/lib/vdr/diseqc.conf
May  2 10:48:31 TV_Server vdr: [4147] loading /var/lib/vdr/unicable.conf
May  2 10:48:31 TV_Server vdr: [4147] loading /var/lib/vdr/channels.conf
May  2 10:48:31 TV_Server vdr: [4147] loading /var/lib/vdr/commands.conf
May  2 10:48:31 TV_Server vdr: [4147] loading /var/lib/vdr/reccmds.conf
May  2 10:48:31 TV_Server vdr: [4147] loading /var/lib/vdr/svdrphosts.conf
May  2 10:48:31 TV_Server vdr: [4147] loading /var/lib/vdr/keymacros.conf
May  2 10:48:31 TV_Server vdr: [4148] video directory scanner thread started (pid=4147, tid=4148)
May  2 10:48:31 TV_Server vdr: [4147] reading EPG data from /var/cache/vdr/epg.data
May  2 10:48:31 TV_Server vdr: [4147] registered source parameters for 'A - ATSC'
May  2 10:48:31 TV_Server vdr: [4147] registered source parameters for 'C - DVB-C'
May  2 10:48:31 TV_Server vdr: [4147] registered source parameters for 'S - DVB-S'
May  2 10:48:31 TV_Server vdr: [4147] registered source parameters for 'T - DVB-T'
May  2 10:48:31 TV_Server vdr: [4147] no DVB device found
May  2 10:48:31 TV_Server vdr: [4147] initializing plugin: xineliboutput (1.0.90-cvs): X11/xine-lib output plugin
May  2 10:48:31 TV_Server vdr: [4147] new device number 9
May  2 10:48:31 TV_Server vdr: [4147] [xine..put] cTimePts: clock_gettime(CLOCK_MONOTONIC): clock resolution 0 us
May  2 10:48:31 TV_Server vdr: [4147] [xine..put] cTimePts: using monotonic clock
May  2 10:48:31 TV_Server vdr: [4147] [xine..put] RTP SSRC: 0x1443d4d9
May  2 10:48:31 TV_Server vdr: [4147] initializing plugin: streamdev-server (0.5.1-git): VDR Streaming Server
May  2 10:48:31 TV_Server vdr: [4147] initializing plugin: conflictcheckonly (0.0.1): Direct access to epgsearch's conflict check menu
May  2 10:48:31 TV_Server vdr: [4147] initializing plugin: vnsiserver (0.9.0): VDR-Network-Streaming-Interface (VNSI) Server
May  2 10:48:31 TV_Server vdr: [4147] initializing plugin: quickepgsearch (0.0.1): Quick search for broadcasts
May  2 10:48:31 TV_Server vdr: [4147] initializing plugin: vdrmanager (0.6): VDR-Manager support plugin
May  2 10:48:31 TV_Server vdr: [4147] initializing plugin: epgsearchonly (0.0.1): Direct access to epgsearch's search menu
May  2 10:48:31 TV_Server vdr: [4147] initializing plugin: epgsearch (1.0.1): search the EPG for repeats and more
May  2 10:48:31 TV_Server vdr: [4147] initializing plugin: eepg (0.0.6pre): Parses Extended EPG data
May  2 10:48:31 TV_Server vdr: [4147] initializing plugin: xvdr (0.9.5): VDR-Network-Streaming-Interface (XVDR) Server
May  2 10:48:31 TV_Server vdr: [4147] initializing plugin: iptv (0.4.2): Experience the IPTV
May  2 10:48:31 TV_Server vdr: [4147] registered source parameters for 'I - IPTV'
May  2 10:48:31 TV_Server vdr: [4147] new device number 10
May  2 10:48:31 TV_Server vdr: [4147] cTimeMs: using monotonic clock (resolution is 1 ns)
May  2 10:48:31 TV_Server vdr: [4147] creating IPTV device 0 (CardIndex=9)
May  2 10:48:31 TV_Server vdr: [4147] setting primary device to 1
May  2 10:48:31 TV_Server vdr: [4147] assuming manual start of VDR
May  2 10:48:31 TV_Server vdr: [4147] SVDRP listening on port 2001
May  2 10:48:31 TV_Server vdr: [4147] setting current skin to "sttng"
May  2 10:48:31 TV_Server vdr: [4147] loading /var/lib/vdr/themes/sttng-default.theme
May  2 10:48:31 TV_Server vdr: [4149] video directory scanner thread started (pid=4147, tid=4149)
May  2 10:48:31 TV_Server vdr: [4148] video directory scanner thread ended (pid=4147, tid=4148)
May  2 10:48:31 TV_Server vdr: [4150] [xine..put] Have CAP_SYS_NICE capability
May  2 10:48:31 TV_Server vdr: [4151] section handler thread started (pid=4147, tid=4151)
May  2 10:48:31 TV_Server vdr: [4147] starting plugin: xineliboutput
May  2 10:48:31 TV_Server vdr: [4149] video directory scanner thread ended (pid=4147, tid=4149)
May  2 10:48:31 TV_Server vdr: [4152] Remote decoder/display server (cXinelibServer) thread started (pid=4147, tid=4152)
May  2 10:48:31 TV_Server vdr: [4152] [xine..put] Have CAP_SYS_NICE capability
May  2 10:48:31 TV_Server vdr: [4152] [xine..put] cXinelibServer priority set successful SCHED_RR 2 [1,99]
May  2 10:48:31 TV_Server vdr: [4152] [xine..put] Binding server to 127.0.0.1:37890
May  2 10:48:31 TV_Server vdr: [4152] [xine..put] Listening on port 37890
May  2 10:48:31 TV_Server vdr: [4152] [xine..put] Listening for UDP broadcasts on port 37890
May  2 10:48:31 TV_Server vdr: [4152] [discovery] BROADCAST: VDR xineliboutput DISCOVERY 1.0#015#012Server port: 37890#015#012Server address: 127.0.0.1#015#012Server version: xineliboutput-1.0.90-cvs#015#012#015
May  2 10:48:32 TV_Server vdr: [4147] [xine..put] cXinelibDevice::StartDevice(): Device started
May  2 10:48:32 TV_Server vdr: [4147] starting plugin: streamdev-server
May  2 10:48:32 TV_Server vdr: [4147] loading /var/lib/vdr/plugins/streamdev-server/streamdevhosts.conf
May  2 10:48:32 TV_Server vdr: [4147] starting plugin: conflictcheckonly
May  2 10:48:32 TV_Server vdr: [4147] starting plugin: vnsiserver
May  2 10:48:32 TV_Server vdr: [4153] streamdev server thread started (pid=4147, tid=4153)
May  2 10:48:32 TV_Server vdr: [4147] VNSI: VNSI Server started
May  2 10:48:32 TV_Server vdr: [4153] Streamdev: Listening (VTP) on port 2004
May  2 10:48:32 TV_Server vdr: [4153] Streamdev: Listening (HTTP) on port 3000
May  2 10:48:32 TV_Server vdr: [4147] VNSI: Channel streaming timeout: 10 seconds
May  2 10:48:32 TV_Server vdr: [4147] starting plugin: quickepgsearch
May  2 10:48:32 TV_Server vdr: [4147] starting plugin: vdrmanager
May  2 10:48:32 TV_Server vdr: [4154] VDR VNSI Server thread started (pid=4147, tid=4154)
May  2 10:48:32 TV_Server vdr: [4147] starting plugin: epgsearchonly
May  2 10:48:32 TV_Server vdr: [4147] starting plugin: epgsearch
May  2 10:48:32 TV_Server vdr: [4147] loading /var/lib/vdr/plugins/epgsearch/epgsearchcats.conf
May  2 10:48:32 TV_Server vdr: [4147] loading /var/lib/vdr/plugins/epgsearch/epgsearchmenu.conf
May  2 10:48:32 TV_Server vdr: [4156] EPGSearch: conflictcheck thread started (pid=4147, tid=4156)
May  2 10:48:32 TV_Server vdr: [4147] starting plugin: eepg
May  2 10:48:32 TV_Server vdr: [4147] Attached EEPG filter to device 0
May  2 10:48:32 TV_Server vdr: [4147] Attached EEPG filter to device 1
May  2 10:48:32 TV_Server vdr: [4147] starting plugin: xvdr
May  2 10:48:32 TV_Server vdr: [4147] XVDR: XVDR Server started
May  2 10:48:32 TV_Server vdr: [4147] XVDR: Channel streaming timeout: 10 seconds
May  2 10:48:32 TV_Server vdr: [4147] starting plugin: iptv
May  2 10:48:32 TV_Server vdr: [4157] VDR XVDR Server thread started (pid=4147, tid=4157)
May  2 10:48:32 TV_Server vdr: [4147] ERROR: /dev/lircd: No such file or directory
May  2 10:48:32 TV_Server vdr: [4147] ERROR: remote control LIRC not ready!
May  2 10:48:32 TV_Server vdr: [4147] switching to channel 1
May  2 10:48:32 TV_Server vdr: [4147] ERROR: setsockopt(): Invalid argument
May  2 10:48:32 TV_Server vdr: [4147] ERROR: setsockopt(): Invalid argument
May  2 10:48:32 TV_Server vdr: [4147] setstatus 0
May  2 10:48:32 TV_Server vdr: [4147] setstatus 1
May  2 10:48:32 TV_Server vdr: [4147] Filter Pid:0,Tid:0 added.
May  2 10:48:32 TV_Server vdr: [4147] setting watchdog timer to 60 seconds
May  2 10:48:32 TV_Server vdr: [4147] OSD size changed to 720x576 @ 1.42222
May  2 10:48:32 TV_Server vdr: [4158] receiver on device 10 thread started (pid=4147, tid=4158)
May  2 10:48:32 TV_Server vdr: [4158] ERROR: setsockopt(): Invalid argument
May  2 10:48:32 TV_Server vdr: [4159] IPTV streamer thread started (pid=4147, tid=4159)
May  2 10:48:32 TV_Server vdr: [4147] [xine..put] cXinelibOsd::CanHandleAreas(): Device does not support ARGB
May  2 10:48:33 TV_Server vdr: [4156] EPGSearch: timer conflict check started
May  2 10:48:33 TV_Server vdr: [4156] EPGSearch: timer conflict check finished
```

Here is the log when I try and stream a channel I setup as an IPTV channel using streamdev on browser 192.168.1.118:3000 and selcting my sample channel, but this is where I am confused.  IPTV, SDV, UPD, etc. 

Channel.conf setup for IPTV
(News4Jax;IPTV:3:S=1|P=1|F=UDP|U=192.168.1.118|A=2004:I:0:0:0:0:0:1:0:0:0)

```
May  2 10:55:10 TV_Server vdr: [4153] Streamdev: Accepted new client (HTTP) 192.168.1.101:36052
May  2 10:55:11 TV_Server vdr: [4147] switching to channel 1
May  2 10:55:11 TV_Server vdr: [4147] info: Channel not available!
May  2 10:55:11 TV_Server vdr: [4147] [xine..put] cXinelibOsd::CanHandleAreas(): Device does not support ARGB
May  2 10:55:11 TV_Server vdr: [4159] IPTV streamer thread ended (pid=4147, tid=4159)
May  2 10:55:11 TV_Server vdr: [4158] receiver on device 10 thread ended (pid=4147, tid=4158)
May  2 10:55:13 TV_Server vdr: [4147] switching to channel 1
May  2 10:55:13 TV_Server vdr: [4147] setstatus 0
May  2 10:55:13 TV_Server vdr: [4147] **ERROR:** setsockopt(): Invalid argument
May  2 10:55:13 TV_Server vdr: [4147] setstatus 0
May  2 10:55:13 TV_Server vdr: [4147] setstatus 1
May  2 10:55:13 TV_Server vdr: [4147] Filter Pid:0,Tid:0 added.
May  2 10:55:13 TV_Server vdr: [4147] info: Streaming active
May  2 10:55:13 TV_Server vdr: [4165] receiver on device 10 thread started (pid=4147, tid=4165)
May  2 10:55:13 TV_Server vdr: [4147] [xine..put] cXinelibOsd::CanHandleAreas(): Device does not support ARGB
May  2 10:55:13 TV_Server vdr: [4165] ERROR: setsockopt(): Invalid argument
May  2 10:55:13 TV_Server vdr: [4166] IPTV streamer thread started (pid=4147, tid=4166)
May  2 10:55:15 TV_Server vdr: [4147] max. latency time 5 seconds
May  2 10:55:15 TV_Server vdr: [4153] setstatus 0
May  2 10:55:15 TV_Server vdr: [4153]** ERROR:** setsockopt(): Invalid argument
May  2 10:55:15 TV_Server vdr: [4153] setstatus 0
May  2 10:55:15 TV_Server vdr: [4153] setstatus 1
May  2 10:55:15 TV_Server vdr: [4153] Filter Pid:0,Tid:0 added.

```

What would I use to scan channels?  most everything I have found has support for dvb devices, but not tuner cards.

Anyone using the Ceton tuner with VDR or TVheadend?

Thank you for taking your time to review my problem or lack of understanding.

---

