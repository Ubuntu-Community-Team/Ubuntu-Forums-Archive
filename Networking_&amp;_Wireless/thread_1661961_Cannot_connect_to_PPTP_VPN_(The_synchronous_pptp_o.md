---
title: "Cannot connect to PPTP VPN (The synchronous pptp option is NOT activated )"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by gongwei on 2011-01-07
Hello, I am trying to connect to a PPTP VPN at work, and I cannot accomplish that. Both server and client are using Ubuntu 10.10. Any ideas? 


```
Jan  7 11:32:26 multicore-dev03 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jan  7 11:32:26 multicore-dev03 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 7608
Jan  7 11:32:26 multicore-dev03 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jan  7 11:32:26 multicore-dev03 NetworkManager: <info>  VPN plugin state changed: 1
Jan  7 11:32:30 multicore-dev03 NetworkManager: <info>  VPN plugin state changed: 3
Jan  7 11:32:30 multicore-dev03 NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received.
Jan  7 11:32:30 multicore-dev03 pppd[7610]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jan  7 11:32:30 multicore-dev03 pppd[7610]: pppd 2.4.5 started by root, uid 0
Jan  7 11:32:30 multicore-dev03 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  7 11:32:30 multicore-dev03 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan  7 11:32:30 multicore-dev03 pppd[7610]: Using interface ppp0
Jan  7 11:32:30 multicore-dev03 pppd[7610]: Connect: ppp0 <--> /dev/pts/1
Jan  7 11:32:30 multicore-dev03 pptp[7614]: nm-pptp-service-7608 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan  7 11:32:30 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan  7 11:32:30 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan  7 11:32:30 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 2048).
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan  7 11:32:31 multicore-dev03 pppd[7610]: Modem hangup
Jan  7 11:32:31 multicore-dev03 pppd[7610]: Connection terminated.
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  VPN plugin failed: 1
Jan  7 11:32:31 multicore-dev03 NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  7 11:32:31 multicore-dev03 pppd[7610]: Exit.
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  VPN plugin failed: 1
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  VPN plugin failed: 1
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  VPN plugin state changed: 6
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  VPN plugin state change reason: 0
Jan  7 11:32:31 multicore-dev03 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan  7 11:32:44 multicore-dev03 NetworkManager: <debug> [1294421564.001626] ensure_killed(): waiting for vpn service pid 7608 to exit
Jan  7 11:32:44 multicore-dev03 NetworkManager: <debug> [1294421564.001718] ensure_killed(): vpn service pid 7608 cleaned up

```

---

### Post by gongwei on 2011-01-07
Hello, I am trying to connect to a PPTP VPN at work, and I cannot accomplish that. Both server and client are using Ubuntu 10.10


```
Jan  7 11:32:26 multicore-dev03 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jan  7 11:32:26 multicore-dev03 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 7608
Jan  7 11:32:26 multicore-dev03 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jan  7 11:32:26 multicore-dev03 NetworkManager: <info>  VPN plugin state changed: 1
Jan  7 11:32:30 multicore-dev03 NetworkManager: <info>  VPN plugin state changed: 3
Jan  7 11:32:30 multicore-dev03 NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received.
Jan  7 11:32:30 multicore-dev03 pppd[7610]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jan  7 11:32:30 multicore-dev03 pppd[7610]: pppd 2.4.5 started by root, uid 0
Jan  7 11:32:30 multicore-dev03 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  7 11:32:30 multicore-dev03 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan  7 11:32:30 multicore-dev03 pppd[7610]: Using interface ppp0
Jan  7 11:32:30 multicore-dev03 pppd[7610]: Connect: ppp0 <--> /dev/pts/1
Jan  7 11:32:30 multicore-dev03 pptp[7614]: nm-pptp-service-7608 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan  7 11:32:30 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan  7 11:32:30 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan  7 11:32:30 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 2048).
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Jan  7 11:32:31 multicore-dev03 pptp[7622]: nm-pptp-service-7608 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan  7 11:32:31 multicore-dev03 pppd[7610]: Modem hangup
Jan  7 11:32:31 multicore-dev03 pppd[7610]: Connection terminated.
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  VPN plugin failed: 1
Jan  7 11:32:31 multicore-dev03 NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  7 11:32:31 multicore-dev03 pppd[7610]: Exit.
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  VPN plugin failed: 1
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  VPN plugin failed: 1
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  VPN plugin state changed: 6
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  VPN plugin state change reason: 0
Jan  7 11:32:31 multicore-dev03 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jan  7 11:32:31 multicore-dev03 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan  7 11:32:44 multicore-dev03 NetworkManager: <debug> [1294421564.001626] ensure_killed(): waiting for vpn service pid 7608 to exit
Jan  7 11:32:44 multicore-dev03 NetworkManager: <debug> [1294421564.001718] ensure_killed(): vpn service pid 7608 cleaned up

```

---

### Post by cariboo on 2011-01-07
I this was a double post due to forums problems, please report the post you want to delete.

---

### Post by gongwei on 2011-01-07
> **cariboo907 said:**
> I this was a double post due to forums problems, please report the post you want to delete.

Please keep this post and delete others. Sorry about that.

---

### Post by gongwei on 2011-01-07
Any body please help me solve this issue?

---

### Post by gongwei on 2011-01-10
up

---

### Post by mixmadmen on 2011-01-11
Hello, 
I'm having a similar issue. 

I've contacted the provider in our DC (Softlayer) where the PPTP box is, and they were unable to replicate the problem using Ubuntu and the exact same settings/method, so I'm wondering if it's some sort of bug. Our DC techs did see some odd behavior, like having to reboot in order for the changes to work, pulling old connection settings at random, etc. but were able to establish lasting connections, so I'm at a loss on my end.

After searching for a couple of days, trying many methods, I and my colleagues can't find any solution. I've noticed that there are others encountering similar issues surrounding a modem hangup. I'm not too familiar with setting up a VPN, but it would appear that a connection is established, but then killed within seconds. Namely this, which keeps showing up at the end of tail -100 /var/log/messages:

```
Jan 11 08:37:04 the-new-hotness pppd[28728]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jan 11 08:37:04 the-new-hotness pppd[28728]: pppd 2.4.5 started by root, uid 0
Jan 11 08:37:04 the-new-hotness pppd[28728]: Using interface ppp0
Jan 11 08:37:04 the-new-hotness pppd[28728]: Connect: ppp0 <--> /dev/pts/1
Jan 11 08:37:25 the-new-hotness pppd[28728]: Modem hangup
Jan 11 08:37:25 the-new-hotness pppd[28728]: Connection terminated.
Jan 11 08:37:25 the-new-hotness pppd[28728]: Exit.
```


 Tried with only *MSCHAP, MSCHAPv2, Uses Point-to-Point, Allow stateful* checked as well as a second time with all of that minus *MSCHAP*, rebooting each time before attempting the connection, but the issue remains. (We have been leaving the routing section default, as we were told it should not have to be touched and should be automatic.)


For comparison:

On the one which **cannot** connect:
Running Ubuntu 10.10, freshly installed a couple days ago. 
The utility in use is NetworkManager Applet 0.8.1
Also, this same PC can dual boot windows, where the PPTP connection works fine, so it isn't an issue between our locations.

On the one which **can** connect:
Ubuntu 10.04
NetworkManager Applet 0.8
They also had one working on 10.10, but it was last tested a week ago.

Maybe some recent update broke something?

Though, something odd that I noticed and may be related, the canonical disk sent to us is labeled 10.10, but the About Ubuntu utility denotes "*You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.*" which is really strange since it's still January, so that date has not yet even come to pass. Some sort of mixup at canonical? If this is a beta, then it may explain why people are having trouble lately. (No, I don't have updates set to allow pre-release or unsupported, and upgrades is set to Normal.)

Oh, and anyway, here are the full logs: 
```
root@the-new-hotness:~# tail -100 /var/log/messages
Jan 11 08:00:24 the-new-hotness kernel: [   11.029456] type=1400 audit(1294758023.114:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=690 comm="apparmor_parser"
Jan 11 08:00:24 the-new-hotness kernel: [   11.029938] type=1400 audit(1294758023.114:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=690 comm="apparmor_parser"
Jan 11 08:00:24 the-new-hotness kernel: [   11.030202] type=1400 audit(1294758023.114:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=690 comm="apparmor_parser"
Jan 11 08:00:24 the-new-hotness kernel: [   11.062616] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 11 08:00:24 the-new-hotness kernel: [   11.116370] lp0: using parport0 (interrupt-driven).
Jan 11 08:00:24 the-new-hotness kernel: [   11.799341] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 11 08:00:24 the-new-hotness kernel: [   11.799353] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jan 11 08:00:24 the-new-hotness kernel: [   11.799434] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
Jan 11 08:00:24 the-new-hotness kernel: [   11.986422] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Jan 11 08:00:24 the-new-hotness kernel: [   12.150476] type=1400 audit(1294758024.238:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=920 comm="apparmor_parser"
Jan 11 08:00:24 the-new-hotness kernel: [   12.150962] type=1400 audit(1294758024.238:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=920 comm="apparmor_parser"
Jan 11 08:00:24 the-new-hotness kernel: [   12.151227] type=1400 audit(1294758024.238:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=920 comm="apparmor_parser"
Jan 11 08:00:24 the-new-hotness kernel: [   12.152588] type=1400 audit(1294758024.242:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=919 comm="apparmor_parser"
Jan 11 08:00:24 the-new-hotness kernel: [   12.153632] type=1400 audit(1294758024.242:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=922 comm="apparmor_parser"
Jan 11 08:00:24 the-new-hotness kernel: [   12.154515] type=1400 audit(1294758024.242:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=925 comm="apparmor_parser"
Jan 11 08:00:24 the-new-hotness kernel: [   12.155107] type=1400 audit(1294758024.242:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=925 comm="apparmor_parser"
Jan 11 08:00:24 the-new-hotness kernel: [   12.308334] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 11 08:00:25 the-new-hotness kernel: [   13.821421] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Jan 11 08:00:26 the-new-hotness kernel: [   14.504359] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Jan 11 08:00:26 the-new-hotness kernel: [   14.513128] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
Jan 11 08:00:26 the-new-hotness kernel: [   14.513131] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Jan 11 08:00:26 the-new-hotness kernel: [   14.513277] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan 11 08:01:53 the-new-hotness pulseaudio[1470]: ratelimit.c: 2 events suppressed
Jan 11 08:05:33 the-new-hotness rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="889" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 11 08:09:57 the-new-hotness kernel: [  587.302490] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Jan 11 08:09:57 the-new-hotness kernel: [  587.303906] SGI XFS Quota Management subsystem
Jan 11 08:09:57 the-new-hotness kernel: [  587.307982] JFS: nTxBlock = 8192, nTxLock = 65536
Jan 11 08:09:57 the-new-hotness kernel: [  587.319689] NTFS driver 2.1.29 [Flags: R/O MODULE].
Jan 11 08:09:57 the-new-hotness kernel: [  587.328659] QNX4 filesystem 0.2.3 registered.
Jan 11 08:09:58 the-new-hotness kernel: [  587.342706] Btrfs loaded
Jan 11 08:09:58 the-new-hotness os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Jan 11 08:09:58 the-new-hotness 50mounted-tests: debug: mounted as ntfs-3g filesystem
Jan 11 08:09:58 the-new-hotness 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jan 11 08:09:58 the-new-hotness 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Jan 11 08:09:58 the-new-hotness 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jan 11 08:09:58 the-new-hotness 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Jan 11 08:09:58 the-new-hotness 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jan 11 08:09:58 the-new-hotness macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Jan 11 08:09:58 the-new-hotness 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jan 11 08:09:58 the-new-hotness 20microsoft: debug: /dev/sda1 is a NTFS partition
Jan 11 08:09:58 the-new-hotness 20microsoft: result: /dev/sda1:Microsoft Windows XP Professional:Windows:chain
Jan 11 08:09:58 the-new-hotness 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Jan 11 08:09:58 the-new-hotness os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jan 11 08:09:58 the-new-hotness os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Jan 11 08:09:58 the-new-hotness 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Jan 11 08:09:58 the-new-hotness os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jan 11 08:09:58 the-new-hotness os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
Jan 11 08:09:58 the-new-hotness 50mounted-tests: debug: /dev/sda6 is a swap partition; skipping
Jan 11 08:09:58 the-new-hotness os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jan 11 08:10:04 the-new-hotness dkms_autoinstaller: nvidia-173 (173.14.28): Installing module on kernel 2.6.35-24-generic.
Jan 11 08:10:28 the-new-hotness dkms_autoinstaller: nvidia-current (260.19.06): Installing module on kernel 2.6.35-24-generic.
Jan 11 08:10:55 the-new-hotness os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Jan 11 08:10:55 the-new-hotness 50mounted-tests: debug: mounted as ntfs-3g filesystem
Jan 11 08:10:55 the-new-hotness 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jan 11 08:10:55 the-new-hotness 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Jan 11 08:10:55 the-new-hotness 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jan 11 08:10:55 the-new-hotness 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Jan 11 08:10:55 the-new-hotness 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jan 11 08:10:55 the-new-hotness macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Jan 11 08:10:55 the-new-hotness 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jan 11 08:10:55 the-new-hotness 20microsoft: debug: /dev/sda1 is a NTFS partition
Jan 11 08:10:55 the-new-hotness 20microsoft: result: /dev/sda1:Microsoft Windows XP Professional:Windows:chain
Jan 11 08:10:55 the-new-hotness 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Jan 11 08:10:55 the-new-hotness os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jan 11 08:10:55 the-new-hotness os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Jan 11 08:10:55 the-new-hotness 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Jan 11 08:10:55 the-new-hotness os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jan 11 08:10:55 the-new-hotness os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
Jan 11 08:10:55 the-new-hotness 50mounted-tests: debug: /dev/sda6 is a swap partition; skipping
Jan 11 08:10:55 the-new-hotness os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jan 11 08:11:02 the-new-hotness kernel: [  651.972293] udev[21189]: starting version 163
Jan 11 08:11:24 the-new-hotness kernel: [  673.584181] audit_printk_skb: 9 callbacks suppressed
Jan 11 08:11:24 the-new-hotness kernel: [  673.584184] type=1400 audit(1294758684.241:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=21495 comm="apparmor_parser"
Jan 11 08:11:24 the-new-hotness kernel: [  673.584347] type=1400 audit(1294758684.245:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=21495 comm="apparmor_parser"
Jan 11 08:11:24 the-new-hotness kernel: [  673.594366] type=1400 audit(1294758684.253:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=21506 comm="apparmor_parser"
Jan 11 08:11:24 the-new-hotness kernel: [  673.594969] type=1400 audit(1294758684.253:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=21506 comm="apparmor_parser"
Jan 11 08:11:32 the-new-hotness kernel: [  682.020752] type=1400 audit(1294758692.681:19): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=21599 comm="apparmor_parser"
Jan 11 08:11:32 the-new-hotness kernel: [  682.021532] type=1400 audit(1294758692.681:20): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=21599 comm="apparmor_parser"
Jan 11 08:11:32 the-new-hotness kernel: [  682.022096] type=1400 audit(1294758692.681:21): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=21599 comm="apparmor_parser"
Jan 11 08:12:09 the-new-hotness kernel: [  718.576116] type=1400 audit(1294758729.233:22): apparmor="STATUS" operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" pid=22449 comm="apparmor_parser"
Jan 11 08:12:09 the-new-hotness kernel: [  718.628964] type=1400 audit(1294758729.289:23): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=22450 comm="apparmor_parser"
Jan 11 08:12:09 the-new-hotness kernel: [  718.629046] type=1400 audit(1294758729.289:24): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=22450 comm="apparmor_parser"
Jan 11 08:12:09 the-new-hotness kernel: [  718.629102] type=1400 audit(1294758729.289:25): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=22450 comm="apparmor_parser"
Jan 11 08:12:09 the-new-hotness kernel: [  718.799588] type=1400 audit(1294758729.457:26): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=22453 comm="apparmor_parser"
Jan 11 08:12:09 the-new-hotness kernel: [  718.799728] type=1400 audit(1294758729.457:27): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=22453 comm="apparmor_parser"
Jan 11 08:12:09 the-new-hotness kernel: [  718.855860] type=1400 audit(1294758729.513:28): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=22454 comm="apparmor_parser"
Jan 11 08:12:12 the-new-hotness kernel: [  721.400409] type=1400 audit(1294758732.061:29): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=22451 comm="apparmor_parser"
Jan 11 08:12:12 the-new-hotness kernel: [  721.401170] type=1400 audit(1294758732.061:30): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=22451 comm="apparmor_parser"
Jan 11 08:12:12 the-new-hotness kernel: [  721.401726] type=1400 audit(1294758732.061:31): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=22451 comm="apparmor_parser"
Jan 11 08:12:14 the-new-hotness kernel: [  724.290544] audit_printk_skb: 21 callbacks suppressed
Jan 11 08:12:14 the-new-hotness kernel: [  724.290546] type=1400 audit(1294758734.949:39): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=22492 comm="apparmor_parser"
Jan 11 08:12:14 the-new-hotness kernel: [  724.291239] type=1400 audit(1294758734.949:40): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=22492 comm="apparmor_parser"
Jan 11 08:12:14 the-new-hotness kernel: [  724.291773] type=1400 audit(1294758734.949:41): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=22492 comm="apparmor_parser"
Jan 11 08:37:04 the-new-hotness pppd[28728]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jan 11 08:37:04 the-new-hotness pppd[28728]: pppd 2.4.5 started by root, uid 0
Jan 11 08:37:04 the-new-hotness pppd[28728]: Using interface ppp0
Jan 11 08:37:04 the-new-hotness pppd[28728]: Connect: ppp0 <--> /dev/pts/1
Jan 11 08:37:25 the-new-hotness pppd[28728]: Modem hangup
Jan 11 08:37:25 the-new-hotness pppd[28728]: Connection terminated.
Jan 11 08:37:25 the-new-hotness pppd[28728]: Exit.
root@the-new-hotness:~# 
```

---

### Post by GapingHeadwound on 2011-01-16
*Exact* problem here, on 10.10.

PPTP VPN was working fine until sometime Wed/Thu. I thought maybe I h0zed it messing about with crap, but then I read mixmadmen's post:

> **mixmadmen said:**
> Hello, 
They also had one working on 10.10, but it was last tested a week ago.

Maybe some recent update broke something?

Though, something odd that I noticed and may be related, the canonical disk sent to us is labeled 10.10, but the About Ubuntu utility denotes "*You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.*" which is really strange since it's still January, so that date has not yet even come to pass. Some sort of mixup at canonical? If this is a beta, then it may explain why people are having trouble lately. (No, I don't have updates set to allow pre-release or unsupported, and upgrades is set to Normal.)


In the time being, I've b0rked everything and have to reinstall network-manager-* so, I'll be back here soon with logs.

---

### Post by nutrapi on 2011-01-27
I haven't been able to use networkmanager for our softlayer pptp vpn connection on 10.10 either :(

---

### Post by jasonbrisbane on 2011-05-17
HI All,

<me too> ;)

I am having the same issue with Ubuntu 10.04.
Using Network-Manager and pptp addin. Also tried vpnc adding too with the same result.

Here are the logs:
> 
May 17 22:39:24 localhost NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
May 17 22:39:24 localhost NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 3225
May 17 22:39:24 localhost NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
May 17 22:39:24 localhost NetworkManager: <info>  VPN plugin state changed: 1
May 17 22:39:28 localhost NetworkManager: <info>  VPN plugin state changed: 3
May 17 22:39:28 localhost NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received.
May 17 22:39:28 localhost pppd[3227]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
May 17 22:39:28 localhost pppd[3227]: pppd 2.4.5 started by root, uid 0
May 17 22:39:28 localhost pppd[3227]: Using interface ppp0
May 17 22:39:28 localhost pppd[3227]: Connect: ppp0 <--> /dev/pts/1
May 17 22:39:28 localhost NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 17 22:39:28 localhost NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 17 22:39:28 localhost pptp[3231]: nm-pptp-service-3225 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
May 17 22:39:28 localhost pppd[3246]: In file /etc/ppp/peers/ppp0: unrecognized option '/dev/modem'
May 17 22:39:49 localhost pptp[3232]: nm-pptp-service-3225 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection timed out
May 17 22:39:49 localhost pptp[3232]: nm-pptp-service-3225 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 205.200.66.91
May 17 22:39:49 localhost pptp[3231]: nm-pptp-service-3225 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
May 17 22:39:49 localhost pppd[3227]: Modem hangup
May 17 22:39:49 localhost pppd[3227]: Connection terminated.
May 17 22:39:49 localhost NetworkManager: <info>  VPN plugin failed: 1
May 17 22:39:49 localhost NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 17 22:39:49 localhost pppd[3227]: Exit.
May 17 22:39:49 localhost NetworkManager: <info>  VPN plugin failed: 1
May 17 22:39:49 localhost NetworkManager: <info>  VPN plugin failed: 1
May 17 22:39:49 localhost NetworkManager: <info>  VPN plugin state changed: 6
May 17 22:39:49 localhost NetworkManager: <info>  VPN plugin state change reason: 0
May 17 22:39:49 localhost NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
May 17 22:39:49 localhost NetworkManager: <info>  Policy set 'Auto ALT255' (wlan0) as default for routing and DNS.
May 17 22:40:02 localhost NetworkManager: <debug> [1305643202.001708] ensure_killed(): waiting for vpn service pid 3225 to exit
May 17 22:40:02 localhost NetworkManager: <debug> [1305643202.001844] ensure_killed(): vpn service pid 3225 cleaned up



Does anyone have any ideas?
Ive tried various settings, including setting refuse-eap in /etc/ppp/pptp-options but to no avail.

With the various errors being reported, I dont know what is an error and what is a notice/info...
Any help?

Regards
Jason Brisbane

---

