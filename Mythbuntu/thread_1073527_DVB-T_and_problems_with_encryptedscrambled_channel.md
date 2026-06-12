---
title: "DVB-T and problems with encrypted/scrambled channels"
date: 2009-02-18
forum: Mythbuntu
---

### Post by joho500 on 2009-02-18
Hi all,

I have a problem with my Technotrend T-1500 card with CI. I can not switch to encrypted channels. The status shows "LMSc" and "partial lock" (translated from dutch). I'm using a conax CAM. Changing the time-out for channel switching to 10 secs didn't help.

My logs:
```
==> /var/log/mythtv/mythbackend.log <==
2009-02-17 18:07:40.683 Main::Registering HttpStatus Extension
2009-02-17 18:07:40.742 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-02-17 18:07:40.812 Enabled verbose msgs:  important general
2009-02-17 18:07:40.875 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-17 18:07:43.529 Reschedule requested for id -1.
2009-02-17 18:07:43.737 Scheduled 0 items in 0.2 = 0.17 match + 0.03 place
2009-02-17 18:07:43.802 scheduler: Scheduled items: Scheduled 0 items in 0.2 = 0.17 match + 0.03 place
2009-02-17 18:07:44.027 Seem to be woken up by USER
2009-02-17 18:07:44.462 MainServer::HandleAnnounce Monitor
2009-02-17 18:07:44.469 adding: mediacenter as a client (events: 0)
2009-02-17 18:07:53.736 MainServer::HandleAnnounce Monitor
2009-02-17 18:07:53.786 adding: mediacenter as a client (events: 0)
2009-02-17 18:07:53.916 MainServer::HandleAnnounce Monitor
2009-02-17 18:07:54.013 adding: mediacenter as a client (events: 1)
2009-02-17 18:09:00.540 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-17 18:10:01.838 MainServer::HandleAnnounce Monitor
2009-02-17 18:10:01.840 adding: mediacenter as a client (events: 0)
2009-02-17 18:20:02.531 MainServer::HandleAnnounce Monitor
2009-02-17 18:20:02.536 adding: mediacenter as a client (events: 0)
2009-02-17 18:24:00.589 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-17 18:30:02.195 MainServer::HandleAnnounce Monitor
2009-02-17 18:30:02.200 adding: mediacenter as a client (events: 0)
2009-02-17 18:39:00.624 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-17 18:40:01.883 MainServer::HandleAnnounce Monitor
2009-02-17 18:40:01.888 adding: mediacenter as a client (events: 0)
2009-02-17 18:46:18.721 MainServer::HandleAnnounce Monitor
2009-02-17 18:46:18.724 adding: mediacenter as a client (events: 0)
2009-02-17 18:46:18.725 MainServer::HandleAnnounce Monitor
2009-02-17 18:46:18.726 adding: mediacenter as a client (events: 1)
2009-02-17 18:46:18.734 MainServer::HandleAnnounce Playback
2009-02-17 18:46:18.742 adding: mediacenter as a client (events: 0)
2009-02-17 18:46:18.757 TVRec(4): Changing from None to WatchingLiveTV
2009-02-17 18:46:18.765 TVRec(4): HW Tuner: 4->4
2009-02-17 18:46:19.954 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-02-17 18:46:20.496 Finished recording That's the question: channel 1002
2009-02-17 18:46:20.505 scheduler: Finished recording: That's the question: channel 1002
2009-02-17 18:46:21.580 Finished recording That's the question: channel 1002
2009-02-17 18:46:21.643 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-02-17 18:46:21.953 Using runtime prefix = /usr
2009-02-17 18:46:21.957 Empty LocalHostName.
2009-02-17 18:46:21.959 Using localhost value of mediacenter
2009-02-17 18:46:21.978 New DB connection, total: 1
2009-02-17 18:46:21.986 Connected to database 'mythconverg' at host: localhost
2009-02-17 18:46:21.989 Closing DB connection named 'DBManager0'
2009-02-17 18:46:21.991 Connected to database 'mythconverg' at host: localhost
2009-02-17 18:46:21.994 New DB connection, total: 2
2009-02-17 18:46:22.005 Connected to database 'mythconverg' at host: localhost
2009-02-17 18:46:22.010 Current Schema Version: 1214
2009-02-17 18:46:22.029 Preview Error: Previewer file '/data/livetv/1002_20090217184618.mpg' is not valid.
2009-02-17 18:46:22.032 Preview Error: Run() file not local: '/data/livetv/1002_20090217184618.mpg'
2009-02-17 18:46:22.047 Preview Error: Preview process not ok.
			fileinfo(/data/livetv/1002_20090217184618.mpg.png) exists: 0 readable: 0 size: 0
2009-02-17 18:46:28.787 TVRec(4): HW Tuner: 4->4
2009-02-17 18:46:31.110 Finished recording That's the question: channel 1002
2009-02-17 18:46:31.164 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-02-17 18:46:31.373 DTVSM(0) Error: Wrong PMT; pmt->pn(112) desired(11)
2009-02-17 18:46:31.376 DTVSM(0) Error: Wrong PMT; pmt->pn(111) desired(11)
2009-02-17 18:46:31.377 DTVSM(0) Error: Wrong PMT; pmt->pn(14) desired(11)
2009-02-17 18:46:31.378 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(11)
2009-02-17 18:46:31.380 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(11)
2009-02-17 18:46:31.388 DTVSM(0) Error: Wrong PMT; pmt->pn(117) desired(11)
2009-02-17 18:46:31.393 DTVSM(0) Error: Wrong PMT; pmt->pn(116) desired(11)
2009-02-17 18:46:31.400 DTVSM(0) Error: Wrong PMT; pmt->pn(115) desired(11)
2009-02-17 18:46:31.404 DTVSM(0) Error: Wrong PMT; pmt->pn(114) desired(11)
2009-02-17 18:46:31.408 DTVSM(0) Error: Wrong PMT; pmt->pn(113) desired(11)
2009-02-17 18:46:31.412 DTVSM(0) Error: Wrong PMT; pmt->pn(15) desired(11)
2009-02-17 18:46:31.411 Using runtime prefix = /usr
2009-02-17 18:46:31.420 Empty LocalHostName.
2009-02-17 18:46:31.424 Using localhost value of mediacenter
2009-02-17 18:46:31.450 New DB connection, total: 1
2009-02-17 18:46:31.458 Connected to database 'mythconverg' at host: localhost
2009-02-17 18:46:31.461 Closing DB connection named 'DBManager0'
2009-02-17 18:46:31.469 Connected to database 'mythconverg' at host: localhost
2009-02-17 18:46:31.478 New DB connection, total: 2
2009-02-17 18:46:31.484 Connected to database 'mythconverg' at host: localhost
2009-02-17 18:46:31.577 Current Schema Version: 1214
2009-02-17 18:46:34.135 AFD: Opened codec 0x97cfe20, id(MPEG2VIDEO) type(Video)
2009-02-17 18:46:34.137 AFD: codec MP3 has 2 channels
2009-02-17 18:46:34.139 AFD: Opened codec 0x97d0410, id(MP3) type(Audio)
2009-02-17 18:46:34.450 Preview: Grabbed preview '/data/livetv/1002_20090217184620.mpg' 704x576@184s
2009-02-17 18:46:35.912 PID 0x3f4 status: Encrypted
2009-02-17 18:46:40.658 PID 0x3f3 status: Encrypted
2009-02-17 18:46:42.847 TVRec(4): Changing from WatchingLiveTV to None
2009-02-17 18:46:42.969 Finished recording Onbekend: channel 1004
2009-02-17 18:46:42.976 scheduler: Last message repeated 2 times: Finished recording: That's the question: channel 1002
2009-02-17 18:46:42.985 scheduler: Finished recording: Onbekend: channel 1004
2009-02-17 18:46:43.016 Finished recording Onbekend: channel 1004
2009-02-17 18:47:51.001 Reschedule requested for id -1.
2009-02-17 18:47:51.040 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2009-02-17 18:47:51.046 scheduler: Last message repeated 1 times: Finished recording: Onbekend: channel 1004
2009-02-17 18:47:51.056 scheduler: Scheduled items: Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2009-02-17 18:48:00.653 Expiring 0 MBytes for 1002 @ Tue Feb 17 18:25:00 2009 => That's the question
2009-02-17 18:48:00.660 autoexpire: Expiring Program: Expiring 0 MBytes for 1002 @ Tue Feb 17 18:25:00 2009 => That's the question
2009-02-17 18:48:00.671 Expiring 1 MBytes for 1002 @ Tue Feb 17 18:25:00 2009 => That's the question
2009-02-17 18:48:00.678 autoexpire: Expiring Program: Expiring 1 MBytes for 1002 @ Tue Feb 17 18:25:00 2009 => That's the question
2009-02-17 18:48:00.681 Expiring 0 MBytes for 1004 @ Tue Feb 17 18:46:30 2009 => Onbekend
2009-02-17 18:48:00.694 autoexpire: Expiring Program: Expiring 0 MBytes for 1004 @ Tue Feb 17 18:46:30 2009 => Onbekend
2009-02-17 18:50:02.723 MainServer::HandleAnnounce Monitor
2009-02-17 18:50:02.728 adding: mediacenter as a client (events: 0)
2009-02-17 18:54:00.705 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

==> /var/log/mythtv/mythfrontend.log <==
2009-02-16 21:36:17.201 FilterManager: failed to load filter 'none', no such filter exists
2009-02-16 21:36:17.203 Couldn't load deinterlace filter none
2009-02-16 21:36:17.214 Realtime priority would require SUID as root.
2009-02-16 21:36:17.308 Video timing method: USleep with busy wait
2009-02-16 21:36:20.159 FilterManager: failed to load filter 'none', no such filter exists
2009-02-16 21:36:20.159 Couldn't load deinterlace filter none
2009-02-16 21:36:20.166 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-02-16 21:36:20.169 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-02-16 21:36:20.566 AFD: Opened codec 0xad4480c0, id(MPEG2VIDEO) type(Video)
2009-02-16 21:36:20.566 AFD: codec MP3 has 2 channels
2009-02-16 21:36:20.566 AFD: Opened codec 0xad449dc0, id(MP3) type(Audio)
2009-02-16 21:36:20.747 Opening audio device 'default'. ch 2(2) sr 48000
2009-02-16 21:36:20.747 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-02-16 21:36:20.809 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2009-02-16 21:36:20.811 NVP: Enabling Audio
2009-02-16 21:36:24.494 [mpeg2video @ 0xb74ba764]skipped MB in I frame at 16 33
2009-02-16 21:36:24.494 [mpeg2video @ 0xb74ba764]Warning MVs not available
2009-02-16 21:36:24.967 [mpeg2video @ 0xb74ba764]mb incr damaged
2009-02-16 21:36:24.970 [mpeg2video @ 0xb74ba764]Warning MVs not available
2009-02-16 21:36:26.202 NVP: prebuffering pause
2009-02-16 21:36:26.249 WriteAudio: buffer underrun
2009-02-16 21:36:26.448 New DB connection, total: 3
2009-02-16 21:36:26.458 Connected to database 'mythconverg' at host: localhost
2009-02-16 21:36:43.356 TV: Attempting to change from WatchingLiveTV to None
2009-02-16 21:36:43.588 TV: Changing from WatchingLiveTV to None
2009-02-16 21:36:43.611 DPMS Reactivated.
2009-02-16 21:36:48.285 Deleting UPnP client...
Starting mythfrontend.real..
2009-02-17 18:07:51.971 New DB connection, total: 2
2009-02-17 18:07:51.972 Connected to database 'mythconverg' at host: localhost
2009-02-17 18:07:51.975 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-02-17 18:07:51.975 Enabled verbose msgs:  important general
2009-02-17 18:07:52.047 Starting mythlcdserver
2009-02-17 18:07:52.571 Connecting to lcd server: localhost:6545 (try 1 of 10)
2009-02-17 18:07:53.128 Connecting to lcd server: localhost:6545 (try 2 of 10)
2009-02-17 18:07:53.629 Connecting to lcd server: localhost:6545 (try 3 of 10)
2009-02-17 18:07:54.129 Connecting to lcd server: localhost:6545 (try 4 of 10)
2009-02-17 18:07:54.630 Connecting to lcd server: localhost:6545 (try 5 of 10)
2009-02-17 18:07:58.445 No theme dir: /home/joho/.mythtv/themes/ProjectGrayhem-wide
2009-02-17 18:07:58.448 Primary screen 0.
2009-02-17 18:07:58.448 Using screen 0, 1280x768 at 0,0
2009-02-17 18:07:58.469 No theme dir: /home/joho/.mythtv/themes/ProjectGrayhem-wide
2009-02-17 18:07:58.470 Switching to wide mode (ProjectGrayhem-wide)
2009-02-17 18:07:58.533 Using the Qt painter
2009-02-17 18:07:58.535 lirc init success using configuration file: /home/joho/.mythtv/lircrc
2009-02-17 18:07:58.537 JoystickMenuClient Error: Joystick disabled - Failed to read /home/joho/.mythtv/joystickmenurc
2009-02-17 18:08:02.847 Specified base font 'medium' does not exist for font clock
2009-02-17 18:08:02.848 Specified base font 'medium' does not exist for font small
2009-02-17 18:08:02.848 Specified base font 'medium' does not exist for font medium
2009-02-17 18:08:02.848 Specified base font 'medium' does not exist for font large
2009-02-17 18:08:02.860 Loading from: /usr/share/mythtv/themes/ProjectGrayhem-wide/base.xml
2009-02-17 18:08:03.036 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-02-17 18:08:03.292 Registering Internal as a media playback plugin.
2009-02-17 18:08:03.563 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-02-17 18:08:03.919 Failed to run 'cdrecord --scanbus'
2009-02-17 18:08:03.924 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-02-17 18:08:03.929 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-02-17 18:08:03.999 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-02-17 18:08:04.357 No theme dir: /home/joho/.mythtv/themes/ProjectGrayhem-wide
2009-02-17 18:46:18.720 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-17 18:46:18.721 Using protocol version 40
2009-02-17 18:46:18.732 TV: Attempting to change from None to WatchingLiveTV
2009-02-17 18:46:18.733 Using protocol version 40
2009-02-17 18:46:20.053 DPMS Deactivated 
2009-02-17 18:46:20.077 NVP: Disabling Audio, params(-1,2,44100)
2009-02-17 18:46:20.131 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-02-17 18:46:20.144 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-02-17 18:46:20.232 OSD Theme Dimensions W: 640 H: 480
2009-02-17 18:46:21.372 TV: Changing from None to WatchingLiveTV
2009-02-17 18:46:21.378 FilterManager: failed to load filter 'none', no such filter exists
2009-02-17 18:46:21.379 Couldn't load deinterlace filter none
2009-02-17 18:46:21.382 Realtime priority would require SUID as root.
2009-02-17 18:46:21.483 Video timing method: USleep with busy wait
2009-02-17 18:46:23.736 NVP: Prebuffer wait timed out 10 times.
2009-02-17 18:46:23.869 FilterManager: failed to load filter 'none', no such filter exists
2009-02-17 18:46:23.869 Couldn't load deinterlace filter none
2009-02-17 18:46:23.876 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-02-17 18:46:23.879 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-02-17 18:46:24.296 AFD: Opened codec 0xa410010, id(MPEG2VIDEO) type(Video)
2009-02-17 18:46:24.296 AFD: codec MP3 has 2 channels
2009-02-17 18:46:24.296 AFD: Opened codec 0xa33d490, id(MP3) type(Audio)
2009-02-17 18:46:24.526 Opening audio device 'default'. ch 2(2) sr 48000
2009-02-17 18:46:24.526 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-02-17 18:46:24.586 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2009-02-17 18:46:24.588 NVP: Enabling Audio
2009-02-17 18:46:29.898 NVP: prebuffering pause
2009-02-17 18:46:29.946 WriteAudio: buffer underrun
2009-02-17 18:46:31.186 New DB connection, total: 3
2009-02-17 18:46:31.187 Connected to database 'mythconverg' at host: localhost
2009-02-17 18:46:42.842 TV: Attempting to change from WatchingLiveTV to None
2009-02-17 18:46:43.074 TV: Changing from WatchingLiveTV to None
2009-02-17 18:46:43.141 DPMS Reactivated.
2009-02-17 18:46:47.546 Deleting UPnP client...

==> /var/log/syslog <==
Feb 17 18:07:25 mediacenter mysqld[10571]: 090217 18:07:25 [Warning] option 'net_buffer_length': unsigned value 8388608 adjusted to 1048576
Feb 17 18:07:26 mediacenter mysqld[10571]: 090217 18:07:26  InnoDB: Started; log sequence number 0 213125
Feb 17 18:07:26 mediacenter mysqld[10571]: 090217 18:07:26 [Note] /usr/sbin/mysqld: ready for connections.
Feb 17 18:07:26 mediacenter mysqld[10571]: Version: '5.0.67-0ubuntu6'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Feb 17 18:07:26 mediacenter /etc/mysql/debian-start[10609]: Upgrading MySQL tables if necessary.
Feb 17 18:07:27 mediacenter /etc/mysql/debian-start[10614]: Looking for 'mysql' in: /usr/bin/mysql
Feb 17 18:07:27 mediacenter /etc/mysql/debian-start[10614]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Feb 17 18:07:27 mediacenter /etc/mysql/debian-start[10614]: This installation of MySQL is already upgraded to 5.0.67, use --force if you still need to run mysql_upgrade
Feb 17 18:07:27 mediacenter /etc/mysql/debian-start[10640]: Checking for insecure root accounts.
Feb 17 18:07:27 mediacenter /etc/mysql/debian-start[10647]: WARNING: mysql.user contains 3 root accounts without password!
Feb 17 18:07:27 mediacenter /etc/mysql/debian-start[10649]: Triggering myisam-recover for all MyISAM tables
Feb 17 18:07:31 mediacenter kernel: [  436.492050] firmware: requesting v4l-cx2341x-enc.fw
Feb 17 18:07:31 mediacenter kernel: [  436.731073] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Feb 17 18:07:31 mediacenter kernel: [  436.928144] ivtv0: Encoder revision: 0x02060039
Feb 17 18:07:32 mediacenter kernel: [  437.672169] tda1004x: setting up plls for 53MHz sampling clock
Feb 17 18:07:33 mediacenter avahi-daemon[9969]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb 17 18:07:33 mediacenter avahi-daemon[9969]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Feb 17 18:07:33 mediacenter kernel: [  438.722205] eth1: remaining active for wake-on-lan
Feb 17 18:07:33 mediacenter avahi-daemon[9969]: Withdrawing address record for fe80::240:f4ff:fe1d:6e65 on eth1.
Feb 17 18:07:33 mediacenter avahi-daemon[9969]: Withdrawing address record for 192.168.1.100 on eth1.
Feb 17 18:07:33 mediacenter dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb 17 18:07:33 mediacenter dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb 17 18:07:33 mediacenter dhclient: All rights reserved.
Feb 17 18:07:33 mediacenter dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb 17 18:07:33 mediacenter dhclient: 
Feb 17 18:07:33 mediacenter kernel: [  439.027555] NET: Registered protocol family 17
Feb 17 18:07:33 mediacenter dhclient: Bind socket to interface: No such device
Feb 17 18:07:33 mediacenter kernel: [  439.035956] eth1: DSPCFG accepted after 0 usec.
Feb 17 18:07:33 mediacenter kernel: [  439.035970] eth1: link up.
Feb 17 18:07:33 mediacenter kernel: [  439.035984] eth1: Setting full-duplex based on negotiated link capability.
Feb 17 18:07:33 mediacenter avahi-daemon[9969]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Feb 17 18:07:33 mediacenter avahi-daemon[9969]: New relevant interface eth1.IPv4 for mDNS.
Feb 17 18:07:33 mediacenter avahi-daemon[9969]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Feb 17 18:07:34 mediacenter acpid: client connected from 11039[114:122] 
Feb 17 18:07:34 mediacenter kernel: [  439.800188] tda1004x: timeout waiting for DSP ready
Feb 17 18:07:34 mediacenter kernel: [  439.801773] tda1004x: found firmware revision 0 -- invalid
Feb 17 18:07:34 mediacenter kernel: [  439.801778] tda1004x: trying to boot from eeprom
Feb 17 18:07:35 mediacenter avahi-daemon[9969]: Registering new address record for fe80::240:f4ff:fe1d:6e65 on eth1.*.
Feb 17 18:07:35 mediacenter bluetoothd[11113]: Bluetooth daemon
Feb 17 18:07:35 mediacenter kernel: [  440.621988] Bluetooth: Core ver 2.13
Feb 17 18:07:35 mediacenter kernel: [  440.622809] NET: Registered protocol family 31
Feb 17 18:07:35 mediacenter kernel: [  440.622814] Bluetooth: HCI device and connection manager initialized
Feb 17 18:07:35 mediacenter kernel: [  440.622820] Bluetooth: HCI socket layer initialized
Feb 17 18:07:35 mediacenter bluetoothd[11113]: Starting SDP server
Feb 17 18:07:35 mediacenter kernel: [  440.662581] Bluetooth: L2CAP ver 2.11
Feb 17 18:07:35 mediacenter kernel: [  440.662590] Bluetooth: L2CAP socket layer initialized
Feb 17 18:07:35 mediacenter kernel: [  440.715166] Bluetooth: SCO (Voice Link) ver 0.6
Feb 17 18:07:35 mediacenter kernel: [  440.715175] Bluetooth: SCO socket layer initialized
Feb 17 18:07:35 mediacenter bluetoothd[11113]: Starting experimental netlink support
Feb 17 18:07:35 mediacenter bluetoothd[11113]: Failed to find Bluetooth netlink family
Feb 17 18:07:35 mediacenter bluetoothd[11113]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Feb 17 18:07:35 mediacenter kernel: [  440.782996] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 17 18:07:35 mediacenter kernel: [  440.783005] Bluetooth: BNEP filters: protocol multicast
Feb 17 18:07:35 mediacenter kernel: [  440.823212] Bridge firewalling registered
Feb 17 18:07:35 mediacenter bluetoothd[11113]: bridge pan0 created
Feb 17 18:07:35 mediacenter kernel: [  440.838440] Bluetooth: RFCOMM socket layer initialized
Feb 17 18:07:35 mediacenter kernel: [  440.838876] Bluetooth: RFCOMM TTY layer initialized
Feb 17 18:07:35 mediacenter kernel: [  440.838882] Bluetooth: RFCOMM ver 1.10
Feb 17 18:07:37 mediacenter kernel: [  442.112248] tda1004x: timeout waiting for DSP ready
Feb 17 18:07:37 mediacenter kernel: [  442.113882] tda1004x: found firmware revision 0 -- invalid
Feb 17 18:07:37 mediacenter kernel: [  442.113887] tda1004x: waiting for firmware upload...
Feb 17 18:07:37 mediacenter kernel: [  442.113894] firmware: requesting dvb-fe-tda10046.fw
Feb 17 18:07:37 mediacenter gdm[11178]: WARNING: Didn't understand `' (expected true or false) 
Feb 17 18:07:37 mediacenter acpid: client connected from 11189[0:0] 
Feb 17 18:07:39 mediacenter kernel: [  443.564707] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Feb 17 18:07:39 mediacenter kernel: [  443.564728] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
Feb 17 18:07:39 mediacenter kernel: [  443.564784] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
Feb 17 18:07:39 mediacenter acpid: client connected from 11189[0:0] 
Feb 17 18:07:39 mediacenter kernel: [  444.905080] tda1004x: found firmware revision 20 -- ok
Feb 17 18:07:44 mediacenter kernel: [  449.364023] eth1: no IPv6 routers present
Feb 17 18:07:45 mediacenter /usr/sbin/cron[11528]: (CRON) INFO (pidfile fd = 3)
Feb 17 18:07:45 mediacenter /usr/sbin/cron[11529]: (CRON) STARTUP (fork ok)
Feb 17 18:07:45 mediacenter kernel: [  450.187715] end_request: I/O error, dev sr0, sector 0
Feb 17 18:07:45 mediacenter kernel: [  450.187731] Buffer I/O error on device sr0, logical block 0
Feb 17 18:07:45 mediacenter kernel: [  450.187737] Buffer I/O error on device sr0, logical block 1
Feb 17 18:07:45 mediacenter kernel: [  450.187740] Buffer I/O error on device sr0, logical block 2
Feb 17 18:07:45 mediacenter kernel: [  450.187744] Buffer I/O error on device sr0, logical block 3
Feb 17 18:07:45 mediacenter kernel: [  450.194784] end_request: I/O error, dev sr0, sector 0
Feb 17 18:07:45 mediacenter kernel: [  450.194793] Buffer I/O error on device sr0, logical block 0
Feb 17 18:07:45 mediacenter kernel: [  450.199699] end_request: I/O error, dev sr0, sector 1024
Feb 17 18:07:45 mediacenter kernel: [  450.199709] Buffer I/O error on device sr0, logical block 128
Feb 17 18:07:45 mediacenter kernel: [  450.210054] end_request: I/O error, dev sr0, sector 1024
Feb 17 18:07:45 mediacenter kernel: [  450.210073] Buffer I/O error on device sr0, logical block 128
Feb 17 18:07:45 mediacenter /usr/sbin/cron[11529]: (CRON) INFO (Running @reboot jobs)
Feb 17 18:07:45 mediacenter kernel: [  450.282469] end_request: I/O error, dev sr0, sector 1024
Feb 17 18:07:45 mediacenter kernel: [  450.282485] Buffer I/O error on device sr0, logical block 128
Feb 17 18:07:45 mediacenter kernel: [  450.289077] end_request: I/O error, dev sr0, sector 1024
Feb 17 18:07:45 mediacenter kernel: [  450.289099] Buffer I/O error on device sr0, logical block 128
Feb 17 18:07:58 mediacenter lircd-0.8.4a[3435]: accepted new client on /dev/lircd
Feb 17 18:09:01 mediacenter /USR/SBIN/CRON[11724]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 17 18:10:01 mediacenter /USR/SBIN/CRON[11770]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Feb 17 18:10:27 mediacenter ntpd[9595]: synchronized to 91.189.94.4, stratum 2
Feb 17 18:10:27 mediacenter ntpd[9595]: kernel time sync status change 0001
Feb 17 18:17:01 mediacenter /USR/SBIN/CRON[11889]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 17 18:20:01 mediacenter /USR/SBIN/CRON[11938]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Feb 17 18:30:01 mediacenter /USR/SBIN/CRON[12101]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Feb 17 18:39:01 mediacenter /USR/SBIN/CRON[12250]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 17 18:40:01 mediacenter /USR/SBIN/CRON[12272]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Feb 17 18:46:49 mediacenter lircd-0.8.4a[3435]: removed client
Feb 17 18:50:01 mediacenter /USR/SBIN/CRON[12518]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)

```

I couldn't find any solution on the net. I hope you can help me.

Cheers,
Joost

---

### Post by jaakan on 2009-02-18
Thats normal with encrypted channels they display "LMSc" and "partial lock". You will only be able to watch NON-encrypted channels.

---

### Post by joho500 on 2009-02-18
As far as I know it should be possible to watch the encrypted channels with the Cam and smartcard I have (see: [http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#TechnoTrend]("http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#TechnoTrend")). But how do I check whether the Common Interface and Cam are working correctly?

Joost

---

### Post by joho500 on 2009-02-27
Finally I put the cards in my Windows PC to test them with Technotrend's own Media Center program and the CAM module wasn't recognized there either. So I send it back fo a nwe set. Hopefully that will work.

I'm closing this thread.

Joost ):P

---

