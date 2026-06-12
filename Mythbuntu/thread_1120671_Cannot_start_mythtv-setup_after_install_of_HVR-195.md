---
title: "Cannot start mythtv-setup after install of HVR-1950"
date: 2009-04-09
forum: Mythbuntu
---

### Post by NeoFax on 2009-04-09
I added a slave backend to my configuration and installed a HVR-1950 USB capture card.  I followed the steps at: [http://sray.squidpower.com/2009/02/18/hauppauge-wintv-hvr-1950-on-linux-mythbuntu-mythtv-analog-digital-video-including-s-video-and-composite-inputs/](http://sray.squidpower.com/2009/02/18/hauppauge-wintv-hvr-1950-on-linux-mythbuntu-mythtv-analog-digital-video-including-s-video-and-composite-inputs/) however, I did not run the mythtv-setup with sudo per the instructions.  Now I cannot open mythtv-setup as it segfaults.  Here are the logs:

```
==> /var/log/mythtv/mythbackend.log <==
2009-04-08 21:10:32.555 Using runtime prefix = /usr
2009-04-08 21:10:32.617 Empty LocalHostName.
2009-04-08 21:10:32.619 Using localhost value of EUROPA
2009-04-08 21:10:32.622 Testing network connectivity to 192.168.1.8
2009-04-08 21:10:32.683 New DB connection, total: 1
2009-04-08 21:10:32.719 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-08 21:10:32.722 Closing DB connection named 'DBManager0'
2009-04-08 21:10:32.726 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-08 21:10:32.729 New DB connection, total: 2
2009-04-08 21:10:32.733 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-08 21:10:32.739 Current Schema Version: 1214
Running as a slave backend.
2009-04-08 21:10:35.546 New DB connection, total: 3
2009-04-08 21:10:35.549 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-08 21:10:36.322 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-04-08 21:10:36.324 DVBChan(4:0) Error: SetChannelByString(2): Failed to initialize multiplex options
2009-04-08 21:10:36.385 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-04-08 21:10:36.387 DVBChan(5:0) Error: SetChannelByString(2): Failed to initialize multiplex options
2009-04-08 21:10:36.496 TVRec(6) Error: Start channel invalid, setting to '58' on input Could not open '' to probe its i instead.
2009-04-08 21:10:36.498 Channel()::Open(): Can't open video device, error "No such file or directory"
2009-04-08 21:10:37.373 mythbackend: Problem with capture cards: Card 6 failed init
2009-04-09 00:00:47.767 Using runtime prefix = /usr
2009-04-09 00:00:47.821 Empty LocalHostName.
2009-04-09 00:00:47.823 Using localhost value of EUROPA
2009-04-09 00:00:47.826 Testing network connectivity to 192.168.1.8
2009-04-09 00:00:47.869 New DB connection, total: 1
2009-04-09 00:00:47.951 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-09 00:00:47.954 Closing DB connection named 'DBManager0'
2009-04-09 00:00:47.957 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-09 00:00:47.966 New DB connection, total: 2
2009-04-09 00:00:47.973 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-09 00:00:47.982 Current Schema Version: 1214
Running as a slave backend.
2009-04-09 00:00:48.202 New DB connection, total: 3
2009-04-09 00:00:48.206 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-09 00:00:48.238 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-04-09 00:00:48.240 DVBChan(4:0) Error: SetChannelByString(2): Failed to initialize multiplex options
2009-04-09 00:00:48.373 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-04-09 00:00:48.375 DVBChan(5:0) Error: SetChannelByString(2): Failed to initialize multiplex options
2009-04-09 00:00:48.509 TVRec(6) Error: Start channel invalid, setting to '58' on input Could not open '' to probe its i instead.
2009-04-09 00:00:48.511 Channel()::Open(): Can't open video device, error "No such file or directory"
2009-04-09 00:00:48.514 mythbackend: Problem with capture cards: Card 6 failed init
2009-04-09 00:10:28.009 Using runtime prefix = /usr
2009-04-09 00:10:28.241 Empty LocalHostName.
2009-04-09 00:10:28.288 Using localhost value of EUROPA
2009-04-09 00:10:28.321 Testing network connectivity to 192.168.1.8
2009-04-09 00:10:28.522 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-04-09 00:10:28.850 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.2009-04-09 00:10:29.022 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error

SSDP::PerformSearch - did not write entire buffer.
...............................................................................
2009-04-09 00:10:31.837 UPnPautoconf() - No UPnP backends found
2009-04-09 00:10:32.090 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name:  
[console is not interactive, using default '']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [d82aP4XM]  
[console is not interactive, using default 'd82aP4XM']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-04-09 00:10:35.791 Could not open settings file /home/mythtv/.mythtv/mysql.txt for writing
2009-04-09 00:10:35.794 Deleting UPnP client...
2009-04-09 00:10:35.798 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-04-09 00:10:35.889 Failed to init MythContext, exiting.
2009-04-09 07:50:48.748 Using runtime prefix = /usr
2009-04-09 07:50:48.802 Empty LocalHostName.
2009-04-09 07:50:48.814 Using localhost value of EUROPA
2009-04-09 07:50:48.912 Testing network connectivity to 192.168.1.8
2009-04-09 07:50:49.004 New DB connection, total: 1
2009-04-09 07:50:49.054 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-09 07:50:49.201 Closing DB connection named 'DBManager0'
2009-04-09 07:50:49.338 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-09 07:50:49.342 New DB connection, total: 2
2009-04-09 07:50:49.344 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-09 07:50:49.456 Current Schema Version: 1214
Running as a slave backend.
2009-04-09 07:50:49.748 New DB connection, total: 3
2009-04-09 07:50:49.752 Connected to database 'mythconverg' at host: 192.168.1.8
2009-04-09 07:50:49.837 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-04-09 07:50:49.839 DVBChan(4:0) Error: SetChannelByString(2): Failed to initialize multiplex options
2009-04-09 07:50:49.893 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-04-09 07:50:49.895 DVBChan(5:0) Error: SetChannelByString(2): Failed to initialize multiplex options
2009-04-09 07:50:50.043 TVRec(6) Error: Start channel invalid, setting to '58' on input Could not open '' to probe its i instead.
2009-04-09 07:50:50.046 Channel()::Open(): Can't open video device, error "No such file or directory"
2009-04-09 07:50:50.049 mythbackend: Problem with capture cards: Card 6 failed init

==> /var/log/syslog <==
Apr  9 04:50:01 EUROPA /USR/SBIN/CRON[19277]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 04:50:01 EUROPA /USR/SBIN/CRON[19288]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 04:52:49 EUROPA ntpd[3667]: kernel time sync status change 4001
Apr  9 05:00:01 EUROPA /USR/SBIN/CRON[19732]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 05:00:01 EUROPA /USR/SBIN/CRON[19735]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Apr  9 05:00:02 EUROPA /USR/SBIN/CRON[19753]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 05:09:01 EUROPA /USR/SBIN/CRON[20295]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr  9 05:09:53 EUROPA ntpd[3667]: kernel time sync status change 0001
Apr  9 05:10:01 EUROPA /USR/SBIN/CRON[20471]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 05:10:01 EUROPA /USR/SBIN/CRON[20485]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 05:17:01 EUROPA /USR/SBIN/CRON[20913]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 05:20:01 EUROPA /USR/SBIN/CRON[21085]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 05:20:01 EUROPA /USR/SBIN/CRON[21098]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 05:30:01 EUROPA /USR/SBIN/CRON[21533]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 05:30:01 EUROPA /USR/SBIN/CRON[21546]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 05:39:01 EUROPA /USR/SBIN/CRON[21977]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr  9 05:40:01 EUROPA /USR/SBIN/CRON[22153]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 05:40:01 EUROPA /USR/SBIN/CRON[22164]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 05:50:01 EUROPA /USR/SBIN/CRON[22598]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 05:50:01 EUROPA /USR/SBIN/CRON[22612]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 06:00:02 EUROPA /USR/SBIN/CRON[23058]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 06:00:02 EUROPA /USR/SBIN/CRON[23061]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 06:00:02 EUROPA /USR/SBIN/CRON[23064]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Apr  9 06:09:01 EUROPA /USR/SBIN/CRON[23618]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr  9 06:10:01 EUROPA /USR/SBIN/CRON[23794]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 06:10:02 EUROPA /USR/SBIN/CRON[23807]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 06:17:01 EUROPA /USR/SBIN/CRON[24234]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 06:20:01 EUROPA /USR/SBIN/CRON[24408]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 06:20:01 EUROPA /USR/SBIN/CRON[24421]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 06:25:01 EUROPA /USR/SBIN/CRON[24846]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Apr  9 06:30:01 EUROPA /USR/SBIN/CRON[25020]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 06:30:01 EUROPA /USR/SBIN/CRON[25032]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 06:35:12 EUROPA ntpd[3667]: kernel time sync status change 4001
Apr  9 06:39:01 EUROPA /USR/SBIN/CRON[25464]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr  9 06:40:01 EUROPA /USR/SBIN/CRON[25640]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 06:40:01 EUROPA /USR/SBIN/CRON[25654]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 06:50:01 EUROPA /USR/SBIN/CRON[26087]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 06:50:01 EUROPA /USR/SBIN/CRON[26098]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 07:00:01 EUROPA /USR/SBIN/CRON[26536]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Apr  9 07:00:01 EUROPA /USR/SBIN/CRON[26558]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 07:00:01 EUROPA /USR/SBIN/CRON[26560]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 07:09:01 EUROPA /USR/SBIN/CRON[26963]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr  9 07:10:01 EUROPA /USR/SBIN/CRON[27146]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 07:10:01 EUROPA /USR/SBIN/CRON[27149]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 07:17:01 EUROPA /USR/SBIN/CRON[27581]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 07:20:01 EUROPA /USR/SBIN/CRON[27753]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 07:20:01 EUROPA /USR/SBIN/CRON[27766]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 07:26:28 EUROPA ntpd[3667]: kernel time sync status change 0001
Apr  9 07:30:01 EUROPA /USR/SBIN/CRON[28213]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Apr  9 07:30:01 EUROPA /USR/SBIN/CRON[28217]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 07:30:01 EUROPA /USR/SBIN/CRON[28220]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 07:30:02 EUROPA anacron[28274]: Anacron 2.3 started on 2009-04-09
Apr  9 07:30:02 EUROPA anacron[28274]: Normal exit (0 jobs run)
Apr  9 07:39:01 EUROPA /USR/SBIN/CRON[28787]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr  9 07:40:01 EUROPA /USR/SBIN/CRON[28968]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 07:40:01 EUROPA /USR/SBIN/CRON[28971]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 07:47:27 EUROPA dbus-daemon: Reloaded configuration
Apr  9 07:47:51 EUROPA kernel: [27470.573264] udev: starting version 141
Apr  9 07:47:52 EUROPA dbus-daemon: Reloaded configuration
Apr  9 07:49:14 EUROPA kernel: [27553.613782] mythtv-setup.re[662]: segfault at fffd0002 ip fffd0002 sp bfcca6bc error 4
Apr  9 07:50:01 EUROPA /USR/SBIN/CRON[710]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 07:50:01 EUROPA /USR/SBIN/CRON[713]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 07:50:52 EUROPA init: Re-executing /sbin/init
Apr  9 07:51:12 EUROPA dbus-daemon: Reloaded configuration
Apr  9 07:51:16 EUROPA NetworkManager: <info>  HAL disappeared 
Apr  9 07:51:19 EUROPA acpid: client connected from 1826[112:120] 
Apr  9 07:51:19 EUROPA NetworkManager: <info>  HAL re-appeared 
Apr  9 07:51:19 EUROPA NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/ssb__null__rfkill_b43_phy0_wlan 
Apr  9 07:51:26 EUROPA dbus-daemon: Reloaded configuration
Apr  9 07:51:28 EUROPA kernel: [27687.406059] mythtv-setup.re[1921]: segfault at 1 ip 00000001 sp bff9191c error 4 in mythtv-setup.real[8048000+23000]
Apr  9 08:00:01 EUROPA /USR/SBIN/CRON[1980]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Apr  9 08:00:01 EUROPA console-kit-daemon[2891]: WARNING: Couldn't read /proc/2890/environ: Failed to open file '/proc/2890/environ': No such file or directory 
Apr  9 08:00:01 EUROPA /USR/SBIN/CRON[2000]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 08:00:01 EUROPA /USR/SBIN/CRON[2003]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 08:00:40 EUROPA ntpd[3667]: kernel time sync status change 4001
Apr  9 08:04:41 EUROPA kernel: [28480.486731] mythtv-setup.re[2725]: segfault at c4 ip 09dc40c2 sp bfcfe67c error 6
Apr  9 08:09:01 EUROPA /USR/SBIN/CRON[2747]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr  9 08:10:01 EUROPA /USR/SBIN/CRON[2869]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 08:10:01 EUROPA /USR/SBIN/CRON[2872]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 08:17:01 EUROPA /USR/SBIN/CRON[3491]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 08:20:01 EUROPA /USR/SBIN/CRON[3663]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 08:20:01 EUROPA /USR/SBIN/CRON[3666]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Apr  9 08:20:41 EUROPA kernel: [29440.014409] mtrr: no MTRR for c8000000,8000000 found
Apr  9 08:20:42 EUROPA acpid: client connected from 4006[0:0] 
Apr  9 08:20:58 EUROPA anacron[4214]: Anacron 2.3 started on 2009-04-09
Apr  9 08:20:58 EUROPA anacron[4214]: Normal exit (0 jobs run)
Apr  9 08:20:59 EUROPA anacron[4266]: Anacron 2.3 started on 2009-04-09
Apr  9 08:20:59 EUROPA anacron[4266]: Normal exit (0 jobs run)
Apr  9 08:21:35 EUROPA kernel: [29494.662359] cx25840' 1-0044: firmware: requesting v4l-cx25840.fw
Apr  9 08:21:37 EUROPA kernel: [29496.652318] cx25840' 1-0044: loaded v4l-cx25840.fw firmware (12559 bytes)
Apr  9 08:21:39 EUROPA kernel: [29498.928669] usb 1-1: firmware: requesting v4l-cx2341x-enc.fw
Apr  9 08:22:05 EUROPA pulseaudio[4675]: reserve-wrap.c: Unable to contact D-Bus session bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-unITudROzF: Connection refused
Apr  9 08:22:28 EUROPA kernel: [29547.069282] cx25840' 1-0044: 0x0000 is not a valid video input!
Apr  9 08:26:58 EUROPA kernel: [29817.017500] mythtv-setup.re[4524]: segfault at 28 ip 00000028 sp bf81497c error 4 in mythtv-setup.real[8048000+23000]
Apr  9 08:27:04 EUROPA kernel: [29823.209308] mythtv-setup.re[4533]: segfault at 28 ip 00000028 sp bfa25b8c error 4 in mythtv-setup.real[8048000+23000]
Apr  9 08:27:08 EUROPA kernel: [29827.942178] mythtv-setup.re[4542]: segfault at 28 ip 00000028 sp bff818ec error 4 in mythtv-setup.real[8048000+23000]
Apr  9 08:27:14 EUROPA kernel: [29833.026171] mythtv-setup.re[4551]: segfault at 28 ip 00000028 sp bffdc94c error 4 in mythtv-setup.real[8048000+23000]
Apr  9 08:27:21 EUROPA kernel: [29840.290728] mythtv-setup.re[4560]: segfault at 28 ip 00000028 sp bfc95dfc error 4 in mythtv-setup.real[8048000+23000]
Apr  9 08:30:01 EUROPA /USR/SBIN/CRON[4582]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr  9 08:30:01 EUROPA /USR/SBIN/CRON[4593]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)

==> /var/log/Xorg.0.log <==
(II) RADEON(0): 	000f0102802115780a0f109758528828
(II) RADEON(0): 	23505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26002115100000190000000000000000
(II) RADEON(0): 	00000000000000000000000000fe004c
(II) RADEON(0): 	475068696c6970734c43440a000000fe
(II) RADEON(0): 	004c503135345730312d544c41390074
(II) RADEON(0): EDID vendor "LPL", prod id 6006
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: NUL  Model: 0  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.358   greenX: 0.292 greenY: 0.595
(II) RADEON(0): blueX: 0.148 blueY: 0.121   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 70  vid: 35457
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 66  vid: 18017
(II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 70  vid: 19041
(II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 72  vid: 19525
(II) RADEON(0): #6: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #7: hsize: 1024  vsize 768  refresh: 66  vid: 18017
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: 17''
(II) RADEON(0): Monitor name: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff003aac000000000000
(II) RADEON(0): 	011001036c221b78eafd06a35b4a9826
(II) RADEON(0): 	1f4f54bfef808180818a714f6146614a
(II) RADEON(0): 	454c81406146302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000fd00324b18
(II) RADEON(0): 	500e000a202020202020000000fc0031
(II) RADEON(0): 	3727270a2020202020202020000000fc
(II) RADEON(0): 	00200a20202020202020202020200005
(II) RADEON(0): EDID vendor "NUL", prod id 0
(II) RADEON(0): EDID vendor "LPL", prod id 6006
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: LPL  Model: 1776  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  289 x 21 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0):  LGPhilipsLCD
(II) RADEON(0):  LP154W01-TLA9
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00320c761700000000
(II) RADEON(0): 	000f0102802115780a0f109758528828
(II) RADEON(0): 	23505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26002115100000190000000000000000
(II) RADEON(0): 	00000000000000000000000000fe004c
(II) RADEON(0): 	475068696c6970734c43440a000000fe
(II) RADEON(0): 	004c503135345730312d544c41390074
(II) RADEON(0): EDID vendor "LPL", prod id 6006
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0

==> /home/terry/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...
09/04/2009 08:20:54 passing arg to libvncserver: -rfbauth
09/04/2009 08:20:54 passing arg to libvncserver: /home/terry/.vnc/passwd
09/04/2009 08:20:54 passing arg to libvncserver: -rfbport
09/04/2009 08:20:54 passing arg to libvncserver: 5900
09/04/2009 08:20:54 x11vnc version: 0.9.3 lastmod: 2007-09-30
09/04/2009 08:20:54 Using X display :0
09/04/2009 08:20:54 
09/04/2009 08:20:54 ------------------ USEFUL INFORMATION ------------------
09/04/2009 08:20:54 X DAMAGE available on display, using it for polling hints.
09/04/2009 08:20:54   To disable this behavior use: '-noxdamage'
09/04/2009 08:20:54 
09/04/2009 08:20:54 XFIXES available on display, resetting cursor mode
09/04/2009 08:20:54   to: '-cursor most'.
09/04/2009 08:20:54   to disable this behavior use: '-cursor arrow'
09/04/2009 08:20:54   or '-noxfixes'.
09/04/2009 08:20:54 using XFIXES for cursor drawing.
09/04/2009 08:20:54 GrabServer control via XTEST.
09/04/2009 08:20:54 
09/04/2009 08:20:54 Scroll Detection: -scrollcopyrect mode is in effect to
09/04/2009 08:20:54   use RECORD extension to try to detect scrolling windows
09/04/2009 08:20:54   (induced by either user keystroke or mouse input).
09/04/2009 08:20:54   If this yields undesired behavior (poor response, painting
09/04/2009 08:20:54   errors, etc) it may be disabled via: '-noscr'
09/04/2009 08:20:54   Also see the -help entry for tuning parameters.
09/04/2009 08:20:54   You can press 3 Alt_L's (Left "Alt" key) in a row to 
09/04/2009 08:20:54   repaint the screen, also see the -fixscreen option for
09/04/2009 08:20:54   periodic repaints.
09/04/2009 08:20:54 
09/04/2009 08:20:54 XKEYBOARD: number of keysyms per keycode 6 is greater
09/04/2009 08:20:54   than 4 and 290 keysyms are mapped above 4.
09/04/2009 08:20:54   Automatically switching to -xkb mode.
09/04/2009 08:20:54   If this makes the key mapping worse you can
09/04/2009 08:20:54   disable it with the "-noxkb" option.
09/04/2009 08:20:54   Also, remember "-remap DEAD" for accenting characters.
09/04/2009 08:20:54 X FBPM extension not supported.
09/04/2009 08:20:54 X display is capable of DPMS.
09/04/2009 08:20:54 --------------------------------------------------------
09/04/2009 08:20:54 
09/04/2009 08:20:54 Default visual ID: 0x21
09/04/2009 08:20:55 Read initial data from X display into framebuffer.
09/04/2009 08:20:55 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
09/04/2009 08:20:55 
09/04/2009 08:20:55 X display :0.0 is 32bpp depth=24 true color
09/04/2009 08:20:55 
09/04/2009 08:20:55 Listening for VNC connections on TCP port 5900
09/04/2009 08:20:55 
09/04/2009 08:20:55 Xinerama is present and active (e.g. multi-head).
09/04/2009 08:20:55 Xinerama: enabling -xwarppointer mode to try to correct
09/04/2009 08:20:55 Xinerama: mouse pointer motion. XTEST+XINERAMA bug.
09/04/2009 08:20:55 Xinerama: Use -noxwarppointer to force XTEST.
09/04/2009 08:20:55 Xinerama: no blackouts needed (screen fills rectangle)
09/04/2009 08:20:55 
09/04/2009 08:20:55 fb read rate: 11 MB/sec
09/04/2009 08:20:55 screen setup finished.
09/04/2009 08:20:55 

The VNC desktop is:      EUROPA:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: http://www.karlrunge.com/x11vnc/#faq-client-caching

/usr/bin/startxfce4: X server already running on display :0
No default user directories
/etc/xdg/xfce4/xinitrc: 59: source: not found
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7

(xfce4-panel:4130): xfce4-panel-WARNING **: xfce4-panel is not running
xfdesktop[4131]: starting up

** (update-notifier:4156): WARNING **: already running?

** (nm-applet:4145): DEBUG: applet_common_device_state_changed
** (nm-applet:4145): DEBUG: applet_common_device_state_changed
** (nm-applet:4145): DEBUG: old state indicates that this was not a disconnect 0

** (gedit:4137): WARNING **: Could not load gedit state file: File is empty

** (update-notifier:4136): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
** (update-notifier:4136): DEBUG: crashreport_check


==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  2.5G  8.1G  24% /
tmpfs                 438M     0  438M   0% /lib/init/rw
varrun                438M  396K  438M   1% /var/run
varlock               438M     0  438M   0% /var/lock
udev                  438M   96K  438M   1% /dev
tmpfs                 438M  112K  438M   1% /dev/shm
lrm                   438M  2.4M  436M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda6              63G  177M   63G   1% /var/lib

==> uname -a <==
Linux EUROPA 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:38:53 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

==> lsusb <==
Bus 001 Device 002: ID 2040:7501 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 003 Device 002: ID 0557:7000 ATEN International Co., Ltd Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 883MiB
     *-cpu
          product: AMD Turion(tm) 64 Mobile Technology ML-32
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.4.2
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=66 mingnt=8
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=64
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=64
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_atiixp latency=64
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-network:0
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:06:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64 module=ssb
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 6
                bus info: pci@0000:06:06.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=[REMOVED] latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
        *-communication
             description: Modem
             product: SB400 AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2 module=snd_atiixp_modem
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
I have checked all of the similar problems here to fix, but short of possibly manually editing the mysql database, I cannot find a fix.  Please HELP!

---

### Post by NeoFax on 2009-04-17
bump

---

### Post by FreeBooteR! on 2009-04-18
ran into the same problem, anyone know what to do?

---

### Post by superm1 on 2009-04-19
Your segfault of mythtv-setup might not actually be caused by this card, but with a bug in the RADEON dri driver.

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898)

Try running mythtv-setup like this:

```
XLIB_SKIP_ARGB_VISUALS=1 mythtv-setup
```

If that works, then this bug is the root cause.

---

