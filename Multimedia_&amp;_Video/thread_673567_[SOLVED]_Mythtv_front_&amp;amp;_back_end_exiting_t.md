---
title: "[SOLVED] Mythtv front &amp;amp; back end exiting to login screen"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by RoyalPro on 2008-01-20
When I try to start either the Mythtv frontend or backend it flashes a text screen and goes to the gdm login screen.  I have tried this from different login accounts and it does the same thing.  I can connect to the backend and use a front end from another computer.  The weird thing is it works if I login to the messed up machine using XDMCP.  I can get both the front end and backend to work (the best it can through XDMCP).  I also tried changed the OpenGL/Qt setting to see if that made a difference, but no luck.  I just can't get it to work locally.
I am going to start reading log files to help me out, but if anyone has answer or help before I figure it out let me know.  I will also post if I figure it out and what was wrong and how I fixed it.

Read last reply

---

### Post by RoyalPro on 2008-01-20
Here are some log file info at the time this started.

(from messages)
Jan 20 12:04:34 umc kernel: [433630.552000] ivtv2: All encoder VBI stream buffers are full. Dropping data.
Jan 20 12:04:34 umc kernel: [433630.552000] ivtv2: Cause: the application is not reading fast enough.
Jan 20 12:07:43 umc gnome-power-manager: (mythuser) GNOME interactive logout because the power button has been pressed
Jan 20 12:08:08 umc kernel: [433845.268000] nfsd: last server has exited
Jan 20 12:08:08 umc kernel: [433845.268000] nfsd: unexporting all filesystems
Jan 20 12:08:08 umc kernel: [433845.272000] RPC: failed to contact local rpcbind server (errno 5).
Jan 20 12:08:09 umc exiting on signal 15
Jan 20 12:09:12 umc syslogd 1.4.1#21ubuntu3: restart

(from kern)
Jan 20 12:04:34 umc kernel: [433630.552000] ivtv2: All encoder VBI stream buffers are full. Dropping data.
Jan 20 12:04:34 umc kernel: [433630.552000] ivtv2: Cause: the application is not reading fast enough.
Jan 20 12:08:08 umc kernel: [433845.268000] nfsd: last server has exited
Jan 20 12:08:08 umc kernel: [433845.268000] nfsd: unexporting all filesystems
Jan 20 12:08:08 umc kernel: [433845.272000] RPC: failed to contact local rpcbind server (errno 5).

(from daemon)
Jan 20 12:05:31 umc lircd-0.8.2[6386]: removed client
Jan 20 12:05:39 umc lircd-0.8.2[6386]: accepted new client on /dev/lircd
Jan 20 12:06:02 umc lircd-0.8.2[6386]: removed client
Jan 20 12:07:25 umc lircd-0.8.2[6386]: accepted new client on /dev/lircd
Jan 20 12:07:36 umc lircd-0.8.2[6386]: removed client
Jan 20 12:07:53 umc init: tty4 main process (4867) killed by TERM signal
Jan 20 12:07:53 umc init: tty5 main process (4868) killed by TERM signal
Jan 20 12:07:53 umc init: tty3 main process (4873) killed by TERM signal
Jan 20 12:07:53 umc init: tty6 main process (4875) killed by TERM signal
Jan 20 12:07:53 umc init: tty2 main process (4871) killed by TERM signal
Jan 20 12:07:53 umc init: tty1 main process (4874) killed by TERM signal
Jan 20 12:07:58 umc avahi-daemon[25473]: Got SIGTERM, quitting.
Jan 20 12:07:58 umc avahi-daemon[25473]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.53.
Jan 20 12:08:02 umc rpc.statd[4591]: Caught signal 15, un-registering and exiting.
Jan 20 12:08:02 umc mysqld[5669]: 080120 12:08:02 [Note] /usr/sbin/mysqld: Normal shutdown
Jan 20 12:08:02 umc mysqld[5669]: 
Jan 20 12:08:02 umc mysqld[5669]: 080120 12:08:02  InnoDB: Starting shutdown...
Jan 20 12:08:04 umc mysqld[5669]: 080120 12:08:04  InnoDB: Shutdown completed; log sequence number 0 43655
Jan 20 12:08:04 umc mysqld[5669]: 080120 12:08:04 [Note] /usr/sbin/mysqld: Shutdown complete
Jan 20 12:08:04 umc mysqld[5669]: 
Jan 20 12:08:04 umc mysqld_safe[31833]: ended

(from syslog)
Jan 20 12:04:34 umc kernel: [433630.552000] ivtv2: All encoder VBI stream buffers are full. Dropping data.
Jan 20 12:04:34 umc kernel: [433630.552000] ivtv2: Cause: the application is not reading fast enough.
Jan 20 12:05:31 umc lircd-0.8.2[6386]: removed client
Jan 20 12:05:39 umc lircd-0.8.2[6386]: accepted new client on /dev/lircd
Jan 20 12:06:02 umc lircd-0.8.2[6386]: removed client
Jan 20 12:07:25 umc lircd-0.8.2[6386]: accepted new client on /dev/lircd
Jan 20 12:07:36 umc lircd-0.8.2[6386]: removed client
Jan 20 12:07:43 umc gnome-power-manager: (marlys) GNOME interactive logout because the power button has been pressed
Jan 20 12:07:53 umc init: tty4 main process (4867) killed by TERM signal
Jan 20 12:07:53 umc init: tty5 main process (4868) killed by TERM signal
Jan 20 12:07:53 umc init: tty3 main process (4873) killed by TERM signal
Jan 20 12:07:53 umc init: tty6 main process (4875) killed by TERM signal
Jan 20 12:07:53 umc init: tty2 main process (4871) killed by TERM signal
Jan 20 12:07:53 umc init: tty1 main process (4874) killed by TERM signal
Jan 20 12:07:58 umc avahi-daemon[25473]: Got SIGTERM, quitting.
Jan 20 12:07:58 umc avahi-daemon[25473]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.53.
Jan 20 12:08:02 umc rpc.statd[4591]: Caught signal 15, un-registering and exiting.
Jan 20 12:08:02 umc mysqld[5669]: 080120 12:08:02 [Note] /usr/sbin/mysqld: Normal shutdown
Jan 20 12:08:02 umc mysqld[5669]: 
Jan 20 12:08:02 umc mysqld[5669]: 080120 12:08:02  InnoDB: Starting shutdown...
Jan 20 12:08:04 umc mysqld[5669]: 080120 12:08:04  InnoDB: Shutdown completed; log sequence number 0 43655
Jan 20 12:08:04 umc mysqld[5669]: 080120 12:08:04 [Note] /usr/sbin/mysqld: Shutdown complete
Jan 20 12:08:04 umc mysqld[5669]: 
Jan 20 12:08:04 umc mysqld_safe[31833]: ended

---

### Post by RoyalPro on 2008-01-20
Simple thing.  One of the updates messed with the Nvidia drivers that I had installed.  I had to reinstall the drivers and all seems good now.

---

