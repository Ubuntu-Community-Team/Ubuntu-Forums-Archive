---
title: "error mess. with pulse audio and surround sound"
date: 2009-04-17
forum: Multimedia Software
---

### Post by dano1 on 2009-04-17
looking at sys log i get an error message for pulse audio and sound is reverting to 2 channels.

```
[HTML]Apr 11 18:36:13 dan-desktop pulseaudio[6159]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 11 18:36:13 dan-desktop pulseaudio[6161]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 11 18:36:13 dan-desktop pulseaudio[6161]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 11 18:48:20 dan-desktop bonobo-activation-server (dan-8535): could not associate with desktop session: Failed to connect to socket /tmp/dbus-nGnlH24Czw: Connection refused
Apr 11 18:49:28 dan-desktop pulseaudio[6199]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 11 18:49:28 dan-desktop pulseaudio[6201]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 11 18:49:28 dan-desktop pulseaudio[6201]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 11 18:52:03 dan-desktop pulseaudio[6207]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 11 18:52:03 dan-desktop pulseaudio[6209]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 11 18:52:03 dan-desktop pulseaudio[6209]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 11 19:45:24 dan-desktop pulseaudio[6233]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 11 19:45:24 dan-desktop pulseaudio[6235]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 11 19:45:24 dan-desktop pulseaudio[6235]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 11 20:03:53 dan-desktop pulseaudio[6179]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 11 20:03:53 dan-desktop pulseaudio[6181]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 11 20:03:53 dan-desktop pulseaudio[6181]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 11 20:03:53 dan-desktop pulseaudio[6181]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 11 20:03:53 dan-desktop pulseaudio[6181]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 11 20:03:53 dan-desktop pulseaudio[6181]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 11 21:38:41 dan-desktop pulseaudio[6186]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 11 21:38:41 dan-desktop pulseaudio[6188]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 11 21:38:41 dan-desktop pulseaudio[6188]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 11 21:38:41 dan-desktop pulseaudio[6188]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 11 21:38:41 dan-desktop pulseaudio[6188]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 11 21:38:41 dan-desktop pulseaudio[6188]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 12 20:58:41 dan-desktop bonobo-activation-server (dan-18241): could not associate with desktop session: Failed to connect to socket /tmp/dbus-i6h0iSECaW: Connection refused
Apr 12 21:00:02 dan-desktop pulseaudio[6168]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 12 21:00:02 dan-desktop pulseaudio[6170]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 12 21:00:02 dan-desktop pulseaudio[6170]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 12 21:00:02 dan-desktop pulseaudio[6170]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 12 21:00:02 dan-desktop pulseaudio[6170]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 12 21:00:02 dan-desktop pulseaudio[6170]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 12 22:07:38 dan-desktop pulseaudio[6206]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 12 22:07:38 dan-desktop pulseaudio[6208]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 12 22:07:38 dan-desktop pulseaudio[6208]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 12 22:07:39 dan-desktop pulseaudio[6208]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 12 22:07:39 dan-desktop pulseaudio[6208]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 12 22:07:39 dan-desktop pulseaudio[6208]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 12 22:12:12 dan-desktop bonobo-activation-server (dan-6846): could not associate with desktop session: Failed to connect to socket /tmp/dbus-VyhosbA4Yf: Connection refused
Apr 12 22:14:42 dan-desktop pulseaudio[6217]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 12 22:14:42 dan-desktop pulseaudio[6219]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 12 22:14:42 dan-desktop pulseaudio[6219]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 12 22:14:42 dan-desktop pulseaudio[6219]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 12 22:14:42 dan-desktop pulseaudio[6219]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 12 22:14:42 dan-desktop pulseaudio[6219]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 12 22:21:39 dan-desktop bonobo-activation-server (dan-7796): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Wbhnw9unv0: Connection refused
Apr 12 22:25:58 dan-desktop pulseaudio[8329]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 12 22:25:58 dan-desktop pulseaudio[8334]: pid.c: Daemon already running.
Apr 12 22:25:58 dan-desktop pulseaudio[8334]: main.c: pa_pid_file_create() failed.
Apr 12 22:25:58 dan-desktop pulseaudio[8329]: main.c: daemon startup failed.
Apr 12 23:04:56 dan-desktop pulseaudio[6241]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 12 23:04:56 dan-desktop pulseaudio[6243]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 12 23:04:56 dan-desktop pulseaudio[6243]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 12 23:04:56 dan-desktop pulseaudio[6243]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 12 23:04:56 dan-desktop pulseaudio[6243]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 12 23:04:56 dan-desktop pulseaudio[6243]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 07:54:51 dan-desktop fsr[11560]: xfs_fsr -m /etc/mtab -t 7200 -f /var/tmp/.fsrlast_xfs ... 
Apr 13 07:54:51 dan-desktop fsr[11561]: /var/lib start inode=0 
Apr 13 07:54:54 dan-desktop fsr[11562]: /var/lib start inode=0 
Apr 13 07:54:54 dan-desktop fsr[11563]: /var/lib start inode=0 
Apr 13 07:54:54 dan-desktop fsr[11564]: /var/lib start inode=0 
Apr 13 07:54:54 dan-desktop fsr[11565]: /var/lib start inode=0 
Apr 13 07:54:54 dan-desktop fsr[11566]: /var/lib start inode=0 
Apr 13 07:54:54 dan-desktop fsr[11567]: /var/lib start inode=0 
Apr 13 07:54:54 dan-desktop fsr[11568]: /var/lib start inode=0 
Apr 13 07:54:54 dan-desktop fsr[11569]: /var/lib start inode=0 
Apr 13 07:54:54 dan-desktop fsr[11570]: /var/lib start inode=0 
Apr 13 07:54:54 dan-desktop fsr[11560]: Completed all 10 passes 
Apr 13 19:47:33 dan-desktop bonobo-activation-server (dan-17099): could not associate with desktop session: Failed to connect to socket /tmp/dbus-qOJhrVJ6hT: Connection refused
Apr 13 19:48:43 dan-desktop pulseaudio[6243]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 19:48:43 dan-desktop pulseaudio[6245]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 13 19:48:43 dan-desktop pulseaudio[6245]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 13 19:48:44 dan-desktop pulseaudio[6245]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 19:48:44 dan-desktop pulseaudio[6245]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 19:48:44 dan-desktop pulseaudio[6245]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 19:59:46 dan-desktop bonobo-activation-server (dan-7020): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Aux540g0sG: Connection refused
Apr 13 19:59:58 dan-desktop pulseaudio[7117]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 19:59:58 dan-desktop pulseaudio[7119]: pid.c: Daemon already running.
Apr 13 19:59:58 dan-desktop pulseaudio[7119]: main.c: pa_pid_file_create() failed.
Apr 13 19:59:58 dan-desktop pulseaudio[7117]: main.c: daemon startup failed.
Apr 13 20:01:15 dan-desktop bonobo-activation-server (dan-7354): could not associate with desktop session: Failed to connect to socket /tmp/dbus-U8KJP07QgJ: Connection refused
Apr 13 20:03:00 dan-desktop pulseaudio[6254]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 20:03:00 dan-desktop pulseaudio[6256]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 13 20:03:00 dan-desktop pulseaudio[6256]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 13 20:03:00 dan-desktop pulseaudio[6256]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 20:03:00 dan-desktop pulseaudio[6256]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 20:03:00 dan-desktop pulseaudio[6256]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 20:03:56 dan-desktop bonobo-activation-server (dan-6479): could not associate with desktop session: Failed to connect to socket /tmp/dbus-hW8y1z050E: Connection refused
Apr 13 20:04:07 dan-desktop pulseaudio[6577]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 20:04:07 dan-desktop pulseaudio[6579]: pid.c: Daemon already running.
Apr 13 20:04:07 dan-desktop pulseaudio[6579]: main.c: pa_pid_file_create() failed.
Apr 13 20:04:07 dan-desktop pulseaudio[6577]: main.c: daemon startup failed.
Apr 13 20:06:29 dan-desktop bonobo-activation-server (dan-6901): could not associate with desktop session: Failed to connect to socket /tmp/dbus-ASotWFJlaJ: Connection refused
Apr 13 20:10:48 dan-desktop pulseaudio[6290]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 20:10:48 dan-desktop pulseaudio[6292]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 13 20:10:48 dan-desktop pulseaudio[6292]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 13 20:10:48 dan-desktop pulseaudio[6292]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 20:10:48 dan-desktop pulseaudio[6292]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 20:10:48 dan-desktop pulseaudio[6292]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 20:32:54 dan-desktop bonobo-activation-server (dan-6877): could not associate with desktop session: Failed to connect to socket /tmp/dbus-g7l0REekNu: Connection refused
Apr 13 20:33:05 dan-desktop pulseaudio[7033]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 20:33:05 dan-desktop pulseaudio[7039]: pid.c: Daemon already running.
Apr 13 20:33:05 dan-desktop pulseaudio[7039]: main.c: pa_pid_file_create() failed.
Apr 13 20:33:05 dan-desktop pulseaudio[7033]: main.c: daemon startup failed.
Apr 13 20:58:45 dan-desktop bonobo-activation-server (dan-8073): could not associate with desktop session: Failed to connect to socket /tmp/dbus-G9IM7snEiI: Connection refused
Apr 13 21:30:02 dan-desktop pulseaudio[6221]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 21:30:02 dan-desktop pulseaudio[6223]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 13 21:30:02 dan-desktop pulseaudio[6223]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 13 21:30:02 dan-desktop pulseaudio[6223]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 21:30:02 dan-desktop pulseaudio[6223]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 21:30:02 dan-desktop pulseaudio[6223]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 21:42:21 dan-desktop pulseaudio[6221]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 21:42:21 dan-desktop pulseaudio[6223]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 13 21:42:21 dan-desktop pulseaudio[6223]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 13 21:42:22 dan-desktop pulseaudio[6223]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 21:42:22 dan-desktop pulseaudio[6223]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 21:42:22 dan-desktop pulseaudio[6223]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 22:02:26 dan-desktop bonobo-activation-server (dan-7155): could not associate with desktop session: Failed to connect to socket /tmp/dbus-spFTWmIllU: Connection refused
Apr 13 22:04:50 dan-desktop pulseaudio[6533]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 22:04:50 dan-desktop pulseaudio[6535]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 13 22:04:50 dan-desktop pulseaudio[6535]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 13 22:04:50 dan-desktop pulseaudio[6535]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 22:04:50 dan-desktop pulseaudio[6535]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 22:04:51 dan-desktop pulseaudio[6535]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 22:05:19 dan-desktop bonobo-activation-server (dan-6722): could not associate with desktop session: Failed to connect to socket /tmp/dbus-vamJV7ubsG: Connection refused
Apr 13 22:06:38 dan-desktop pulseaudio[6233]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 22:06:38 dan-desktop pulseaudio[6235]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 13 22:06:38 dan-desktop pulseaudio[6235]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 13 22:06:39 dan-desktop pulseaudio[6235]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 22:06:39 dan-desktop pulseaudio[6235]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 22:06:39 dan-desktop pulseaudio[6235]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 22:08:22 dan-desktop bonobo-activation-server (dan-6546): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Sg0SF3j3se: Connection refused
Apr 13 22:09:35 dan-desktop pulseaudio[6222]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 22:09:35 dan-desktop pulseaudio[6224]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 13 22:09:35 dan-desktop pulseaudio[6224]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 13 22:09:35 dan-desktop pulseaudio[6224]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 22:09:35 dan-desktop pulseaudio[6224]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 22:09:35 dan-desktop pulseaudio[6224]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 22:32:13 dan-desktop bonobo-activation-server (dan-7110): could not associate with desktop session: Failed to connect to socket /tmp/dbus-A5PVMrqpzB: Connection refused
Apr 13 22:45:57 dan-desktop pulseaudio[6281]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 22:45:57 dan-desktop pulseaudio[6283]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 13 22:45:57 dan-desktop pulseaudio[6283]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 13 22:45:57 dan-desktop pulseaudio[6283]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 22:45:57 dan-desktop pulseaudio[6283]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 22:45:57 dan-desktop pulseaudio[6283]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 22:46:33 dan-desktop bonobo-activation-server (dan-6487): could not associate with desktop session: Failed to connect to socket /tmp/dbus-8njRF0E6Ay: Connection refused
Apr 13 22:47:44 dan-desktop pulseaudio[6233]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 13 22:47:44 dan-desktop pulseaudio[6235]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 13 22:47:44 dan-desktop pulseaudio[6235]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 13 22:47:45 dan-desktop pulseaudio[6235]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 13 22:47:45 dan-desktop pulseaudio[6235]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 13 22:47:45 dan-desktop pulseaudio[6235]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 14 08:05:54 dan-desktop fsr[19333]: xfs_fsr -m /etc/mtab -t 7200 -f /var/tmp/.fsrlast_xfs ... 
Apr 14 08:05:54 dan-desktop fsr[19334]: /var/lib start inode=0 
Apr 14 08:05:57 dan-desktop fsr[19335]: /var/lib start inode=0 
Apr 14 08:05:57 dan-desktop fsr[19336]: /var/lib start inode=0 
Apr 14 08:05:57 dan-desktop fsr[19337]: /var/lib start inode=0 
Apr 14 08:05:57 dan-desktop fsr[19338]: /var/lib start inode=0 
Apr 14 08:05:57 dan-desktop fsr[19339]: /var/lib start inode=0 
Apr 14 08:05:57 dan-desktop fsr[19340]: /var/lib start inode=0 
Apr 14 08:05:57 dan-desktop fsr[19341]: /var/lib start inode=0 
Apr 14 08:05:57 dan-desktop fsr[19342]: /var/lib start inode=0 
Apr 14 08:05:57 dan-desktop fsr[19343]: /var/lib start inode=0 
Apr 14 08:05:57 dan-desktop fsr[19333]: Completed all 10 passes 
Apr 14 09:14:14 dan-desktop bonobo-activation-server (dan-20981): could not associate with desktop session: Failed to connect to socket /tmp/dbus-jvz6VEzU8v: Connection refused
Apr 14 09:26:33 dan-desktop pulseaudio[6224]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 14 09:26:33 dan-desktop pulseaudio[6226]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 14 09:26:33 dan-desktop pulseaudio[6226]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 14 09:26:33 dan-desktop pulseaudio[6226]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 14 09:26:33 dan-desktop pulseaudio[6226]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 14 09:26:33 dan-desktop pulseaudio[6226]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 14 10:15:27 dan-desktop pulseaudio[6399]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 14 10:15:27 dan-desktop pulseaudio[6401]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 14 10:15:27 dan-desktop pulseaudio[6401]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 14 10:15:28 dan-desktop pulseaudio[6401]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 14 10:15:28 dan-desktop pulseaudio[6401]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 14 10:15:28 dan-desktop pulseaudio[6401]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 15 01:05:44 dan-desktop pulseaudio[6820]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 15 01:05:44 dan-desktop pulseaudio[6856]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 15 01:05:44 dan-desktop pulseaudio[6856]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 15 01:05:44 dan-desktop pulseaudio[6856]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 15 01:05:44 dan-desktop pulseaudio[6856]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 15 01:05:44 dan-desktop pulseaudio[6856]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 15 01:14:02 dan-desktop fsr[7370]: xfs_fsr -m /etc/mtab -t 7200 -f /var/tmp/.fsrlast_xfs ... 
Apr 15 01:14:02 dan-desktop fsr[7371]: /var/lib start inode=0 
Apr 15 01:14:03 dan-desktop fsr[7372]: /var/lib start inode=0 
Apr 15 01:14:04 dan-desktop fsr[7373]: /var/lib start inode=0 
Apr 15 01:14:04 dan-desktop fsr[7374]: /var/lib start inode=0 
Apr 15 01:14:04 dan-desktop fsr[7375]: /var/lib start inode=0 
Apr 15 01:14:04 dan-desktop fsr[7376]: /var/lib start inode=0 
Apr 15 01:14:04 dan-desktop fsr[7377]: /var/lib start inode=0 
Apr 15 01:14:04 dan-desktop fsr[7378]: /var/lib start inode=0 
Apr 15 01:14:04 dan-desktop fsr[7379]: /var/lib start inode=0 
Apr 15 01:14:04 dan-desktop fsr[7380]: /var/lib start inode=0 
Apr 15 01:14:04 dan-desktop fsr[7370]: Completed all 10 passes 
Apr 15 01:15:27 dan-desktop bonobo-activation-server (dan-7518): could not associate with desktop session: Failed to connect to socket /tmp/dbus-4VJKengHWB: Connection refused
Apr 15 01:17:09 dan-desktop pulseaudio[8113]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 15 01:17:09 dan-desktop pulseaudio[8120]: pid.c: Daemon already running.
Apr 15 01:17:09 dan-desktop pulseaudio[8120]: main.c: pa_pid_file_create() failed.
Apr 15 01:17:09 dan-desktop pulseaudio[8113]: main.c: daemon startup failed.
Apr 15 02:02:52 dan-desktop pulseaudio[6688]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 15 02:02:52 dan-desktop pulseaudio[6690]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 15 02:02:52 dan-desktop pulseaudio[6690]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 15 02:02:52 dan-desktop pulseaudio[6690]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 15 02:02:52 dan-desktop pulseaudio[6690]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 15 02:02:52 dan-desktop pulseaudio[6690]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 16 00:12:22 dan-desktop pulseaudio[6234]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 16 00:12:22 dan-desktop pulseaudio[6236]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 16 00:12:22 dan-desktop pulseaudio[6236]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 16 00:12:22 dan-desktop pulseaudio[6236]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 16 00:12:22 dan-desktop pulseaudio[6236]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 16 00:12:22 dan-desktop pulseaudio[6236]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 16 00:49:08 dan-desktop fsr[7116]: xfs_fsr -m /etc/mtab -t 7200 -f /var/tmp/.fsrlast_xfs ... 
Apr 16 00:49:08 dan-desktop fsr[7117]: /var/lib start inode=0 
Apr 16 00:49:09 dan-desktop fsr[7118]: /var/lib start inode=0 
Apr 16 00:49:09 dan-desktop fsr[7119]: /var/lib start inode=0 
Apr 16 00:49:09 dan-desktop fsr[7120]: /var/lib start inode=0 
Apr 16 00:49:09 dan-desktop fsr[7121]: /var/lib start inode=0 
Apr 16 00:49:09 dan-desktop fsr[7122]: /var/lib start inode=0 
Apr 16 00:49:10 dan-desktop fsr[7123]: /var/lib start inode=0 
Apr 16 00:49:10 dan-desktop fsr[7124]: /var/lib start inode=0 
Apr 16 00:49:10 dan-desktop fsr[7125]: /var/lib start inode=0 
Apr 16 00:49:10 dan-desktop fsr[7126]: /var/lib start inode=0 
Apr 16 00:49:10 dan-desktop fsr[7116]: Completed all 10 passes 
Apr 16 01:09:56 dan-desktop pulseaudio[6294]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 16 01:09:56 dan-desktop pulseaudio[6296]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 16 01:09:56 dan-desktop pulseaudio[6296]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 16 01:09:56 dan-desktop pulseaudio[6296]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 16 01:09:56 dan-desktop pulseaudio[6296]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 16 01:09:56 dan-desktop pulseaudio[6296]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 16 08:57:05 dan-desktop pulseaudio[6237]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 16 08:57:05 dan-desktop pulseaudio[6239]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 16 08:57:05 dan-desktop pulseaudio[6239]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 16 08:57:05 dan-desktop pulseaudio[6239]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 16 08:57:05 dan-desktop pulseaudio[6239]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 16 08:57:05 dan-desktop pulseaudio[6239]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 16 22:04:45 dan-desktop bonobo-activation-server (dan-12074): could not associate with desktop session: Failed to connect to socket /tmp/dbus-4poJRW2BPL: Connection refused
Apr 16 22:10:11 dan-desktop pulseaudio[6417]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 16 22:10:11 dan-desktop pulseaudio[6419]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 16 22:10:11 dan-desktop pulseaudio[6419]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 16 22:10:12 dan-desktop pulseaudio[6419]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 16 22:10:12 dan-desktop pulseaudio[6419]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 16 22:10:12 dan-desktop pulseaudio[6419]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 16 23:29:14 dan-desktop bonobo-activation-server (dan-9080): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Z4C8bGj6fb: Connection refused
Apr 16 23:30:21 dan-desktop pulseaudio[6241]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 16 23:30:21 dan-desktop pulseaudio[6243]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 16 23:30:21 dan-desktop pulseaudio[6243]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 16 23:30:22 dan-desktop pulseaudio[6243]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 16 23:30:22 dan-desktop pulseaudio[6243]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 16 23:30:22 dan-desktop pulseaudio[6243]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 16 23:47:27 dan-desktop bonobo-activation-server (dan-6868): could not associate with desktop session: Failed to connect to socket /tmp/dbus-yKgHpCPi2t: Connection refused
Apr 17 00:02:23 dan-desktop pulseaudio[6228]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 17 00:02:23 dan-desktop pulseaudio[6230]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 17 00:02:23 dan-desktop pulseaudio[6230]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 17 00:02:24 dan-desktop pulseaudio[6230]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 17 00:02:24 dan-desktop pulseaudio[6230]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 00:02:24 dan-desktop pulseaudio[6230]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 00:48:13 dan-desktop fsr[7385]: xfs_fsr -m /etc/mtab -t 7200 -f /var/tmp/.fsrlast_xfs ... 
Apr 17 00:48:13 dan-desktop fsr[7386]: /var/lib start inode=0 
Apr 17 00:48:13 dan-desktop fsr[7387]: /var/lib start inode=0 
Apr 17 00:48:13 dan-desktop fsr[7388]: /var/lib start inode=0 
Apr 17 00:48:13 dan-desktop fsr[7389]: /var/lib start inode=0 
Apr 17 00:48:13 dan-desktop fsr[7390]: /var/lib start inode=0 
Apr 17 00:48:13 dan-desktop fsr[7391]: /var/lib start inode=0 
Apr 17 00:48:13 dan-desktop fsr[7392]: /var/lib start inode=0 
Apr 17 00:48:13 dan-desktop fsr[7393]: /var/lib start inode=0 
Apr 17 00:48:14 dan-desktop fsr[7394]: /var/lib start inode=0 
Apr 17 00:48:14 dan-desktop fsr[7395]: /var/lib start inode=0 
Apr 17 00:48:14 dan-desktop fsr[7385]: Completed all 10 passes 
Apr 17 02:05:28 dan-desktop bonobo-activation-server (dan-8529): could not associate with desktop session: Failed to connect to socket /tmp/dbus-odpPEsSpsZ: Connection refused
Apr 17 02:06:43 dan-desktop pulseaudio[6224]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 17 02:06:43 dan-desktop pulseaudio[6226]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 17 02:06:43 dan-desktop pulseaudio[6226]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 17 02:06:43 dan-desktop pulseaudio[6226]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 17 02:06:43 dan-desktop pulseaudio[6226]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 02:06:43 dan-desktop pulseaudio[6226]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 02:09:27 dan-desktop pulseaudio[6272]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 17 02:09:27 dan-desktop pulseaudio[6274]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 17 02:09:27 dan-desktop pulseaudio[6274]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 17 02:09:27 dan-desktop pulseaudio[6274]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 17 02:09:27 dan-desktop pulseaudio[6274]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 02:09:27 dan-desktop pulseaudio[6274]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 02:33:19 dan-desktop bonobo-activation-server (dan-6871): could not associate with desktop session: Failed to connect to socket /tmp/dbus-uI2pfSNHsf: Connection refused
Apr 17 02:53:36 dan-desktop pulseaudio[6858]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 17 02:53:36 dan-desktop pulseaudio[6895]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 17 02:53:36 dan-desktop pulseaudio[6895]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 17 02:53:36 dan-desktop pulseaudio[6895]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 17 02:53:36 dan-desktop pulseaudio[6895]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 02:53:36 dan-desktop pulseaudio[6895]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 03:04:57 dan-desktop pulseaudio[6241]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 17 03:04:57 dan-desktop pulseaudio[6243]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 17 03:04:57 dan-desktop pulseaudio[6243]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 17 03:04:57 dan-desktop pulseaudio[6243]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 17 03:04:57 dan-desktop pulseaudio[6243]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 03:04:57 dan-desktop pulseaudio[6243]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 08:31:28 dan-desktop pulseaudio[6242]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 17 08:31:28 dan-desktop pulseaudio[6244]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 17 08:31:28 dan-desktop pulseaudio[6244]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 17 08:31:28 dan-desktop pulseaudio[6244]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 17 08:31:28 dan-desktop pulseaudio[6244]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 08:31:28 dan-desktop pulseaudio[6244]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 15:54:59 dan-desktop bonobo-activation-server (dan-11943): could not associate with desktop session: Failed to connect to socket /tmp/dbus-HRh9BzkETw: Connection refused
Apr 17 16:05:28 dan-desktop pulseaudio[6258]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 17 16:05:28 dan-desktop pulseaudio[6260]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 17 16:05:28 dan-desktop pulseaudio[6260]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 17 16:05:28 dan-desktop pulseaudio[6260]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 17 16:05:28 dan-desktop pulseaudio[6260]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 16:05:28 dan-desktop pulseaudio[6260]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 16:53:47 dan-desktop pulseaudio[6273]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 17 16:53:47 dan-desktop pulseaudio[6275]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 17 16:53:47 dan-desktop pulseaudio[6275]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 17 16:53:48 dan-desktop pulseaudio[6275]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 17 16:53:48 dan-desktop pulseaudio[6275]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 16:53:48 dan-desktop pulseaudio[6275]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 16:57:14 dan-desktop bonobo-activation-server (dan-6542): could not associate with desktop session: Failed to connect to socket /tmp/dbus-N4IYG8oqK8: Connection refused
Apr 17 17:22:16 dan-desktop pulseaudio[6345]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 17 17:22:16 dan-desktop pulseaudio[6347]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 17 17:22:16 dan-desktop pulseaudio[6347]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 17 17:22:16 dan-desktop pulseaudio[6347]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 17 17:22:16 dan-desktop pulseaudio[6347]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 17:22:16 dan-desktop pulseaudio[6347]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 17:41:18 dan-desktop bonobo-activation-server (dan-6920): could not associate with desktop session: Failed to connect to socket /tmp/dbus-pCNm9ap8Hp: Connection refused
Apr 17 17:46:07 dan-desktop pulseaudio[6227]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 17 17:46:07 dan-desktop pulseaudio[6229]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 17 17:46:07 dan-desktop pulseaudio[6229]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 17 17:46:07 dan-desktop pulseaudio[6229]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
Apr 17 17:46:07 dan-desktop pulseaudio[6229]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
Apr 17 17:46:07 dan-desktop pulseaudio[6229]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.
[/HTML]
```
seems like im getting 6 channeel sound but doesnt show in alsamixer. Any advise ?
TIA, danny

---

### Post by dano1 on 2009-04-19
bump

---

### Post by markbuntu on 2009-04-19
[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

That should get your surround sound working
The other messages you can fix by going to System/Administration/Users and Groups and making your users and root members of the following groups
pulse
pulse-rt
pulse-access

---

### Post by dano1 on 2009-04-19
nope didnt work. followed your guide and this. Still the same err. mess.

see alsamixer output:



should i retry following your user guide? also have installed onboard sound hw:0 and a pci sound card nad wish to use onboard sound(sounds better ;) Should i remove the pci card ?

Tried to force alsa reload and got same error message:

W: ltdl-bind-now.c: Failed to find original dlopen loader.

any help appreciated.

thanks, danny

---

### Post by markbuntu on 2009-04-20
What does aplay -l tell you?

---

### Post by dano1 on 2009-04-20
output of aplay-l

dan@dan-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dan@dan-desktop:~$ 

now i've lost the speaker icon on the taskbar. hmmm
any help appreciated.

Thanks for your trouble mark. Also planning on upgrading to9.04 in a couple of days. Will this solve mu sound issues ?

TIA, danny

---

