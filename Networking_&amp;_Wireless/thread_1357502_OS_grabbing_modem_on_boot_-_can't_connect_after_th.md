---
title: "OS grabbing modem on boot - can't connect after that"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by ayoungmennonite on 2009-12-17
I have some experience with Linux, but I am new to the Ubuntu family. I chose Kubuntu because my family has gotten used to KDE under Slackware, but I got tired of trying to work out the dependencies on my own, so I switched to another distribution, and Kubuntu was it.

Our problem is that we are using an old external modem, and something in the bootup process is grabbing the modem and not releasing it, so when we try to connect, we are not connected to our ISP, but the dialing software cannot connect to the modem, as it is already in use. (I tried to use kppp and was getting errors without realizing the modem was already in use, so I've installed gnome-ppp).

If I open a terminal and do something to the effect of `pon; sleep 5; poff` I can clear the modem. Then gnome-ppp can connect.

But my wife HATES terminal windows, and I'd rather figure out how to get this working properly anyway.

I looked in /etc/init.d and tried to turn off the executable for anything that seemed to be related, but I guess I am missing something. Could anyone please point me toward the correct script? Thanks.

This is the `ls -l` of init.d:

[FONT=Courier New]total 224
drwxr-xr-x   2 root root  4096 2009-11-17 17:16 .
drwxr-xr-x 121 root root  8192 2009-11-30 05:28 ..
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 acpid -> /lib/init/upstart-job
-rwxr-xr-x   1 root root   763 2009-10-13 03:45 acpi-support
-rwxr-xr-x   1 root root 10342 2009-10-20 04:26 alsa-utils
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 anacron -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  3314 2009-10-16 23:39 apparmor
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 apport -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 atd -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 avahi-daemon -> /lib/init/upstart-job
-rw-r--r--   1 root root  1091 2009-09-24 18:40 bluetooth
-rwxr-xr-x   1 root root  2341 2009-09-07 13:58 bootlogd
-rwxr-xr-x   1 root root  2041 2009-10-13 18:54 brltty
-rwxr-xr-x   1 root root  1670 2009-07-06 06:10 console-setup
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 cron -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  3072 2009-10-15 14:15 cups
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 dbus -> /lib/init/upstart-job
-rw-r--r--   1 root root    24 2009-10-28 16:32 .depend.boot
-rw-r--r--   1 root root    24 2009-10-28 16:32 .depend.start
-rw-r--r--   1 root root    10 2009-10-28 16:32 .depend.stop
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 dmesg -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  1235 2009-02-20 11:56 dns-clean
-rwxr-xr-x   1 root root  1105 2009-10-23 19:31 grub-common
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 hal -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  1329 2009-09-07 13:58 halt
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 hwclock -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 hwclock-save -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 kdm -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  1851 2009-09-24 06:28 kerneloops
-rwxr-xr-x   1 root root  1404 2009-07-06 06:10 keyboard-setup
-rwxr-xr-x   1 root root  1293 2009-09-07 13:58 killprocs
-rw-r--r--   1 root root  2290 2009-10-06 18:02 laptop-mode
-rw-r--r--   1 root root     0 2009-10-28 16:32 .legacy-bootordering
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 module-init-tools -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  2070 2009-09-14 16:11 networking
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 network-manager -> /lib/init/upstart-job
-rwxr-xr-x   1 root root   882 2009-09-07 13:58 ondemand
-rw-r--r--   1 root root  2398 2009-03-09 11:41 pcmciautils
-rwxr-xr-x   1 root root   665 2009-06-22 02:18 policykit
-rwxr-xr-x   1 root root   420 2009-02-20 11:24 pppd-dns
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 procps -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  8863 2009-09-07 13:58 rc
-rwxr-xr-x   1 root root   801 2009-09-07 13:58 rc.local
-rwxr-xr-x   1 root root   117 2009-09-07 13:58 rcS
-rw-r--r--   1 root root  1510 2009-09-07 13:58 README
-rwxr-xr-x   1 root root   639 2009-09-07 13:58 reboot
-rwxr-xr-x   1 root root  4310 2009-06-25 08:12 rsync
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 rsyslog -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 rsyslog-kmsg -> /lib/init/upstart-job
-rw-r--r--   1 root root  2262 2009-10-14 11:42 saned
-rwxr-xr-x   1 root root  1055 2009-07-06 00:35 screen-cleanup
-rwxr-xr-x   1 root root  2283 2009-09-07 13:58 sendsigs
-rwxr-xr-x   1 root root   590 2009-09-07 13:58 single
-rw-r--r--   1 root root  4271 2009-09-07 13:58 skeleton
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 sreadahead -> /lib/init/upstart-job
-rwxr-xr-x   1 root root   519 2009-09-07 13:58 stop-bootlogd
-rwxr-xr-x   1 root root  1095 2009-09-07 13:58 stop-bootlogd-single
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 udev -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 udev-finish -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 udevmonitor -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 udevtrigger -> /lib/init/upstart-job
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 ufw -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  2746 2009-10-13 23:15 umountfs
-rwxr-xr-x   1 root root  2075 2009-10-13 23:16 umountnfs.sh
-rwxr-xr-x   1 root root  1683 2009-10-13 23:20 umountroot
-rw-r--r--   1 root root 12288 2009-10-13 23:20 .umountroot.swp
-rwxr-xr-x   1 root root   841 2009-07-20 06:47 unattended-upgrades
-rwxr-xr-x   1 root root  1997 2009-09-07 13:58 urandom
lrwxrwxrwx   1 root root    21 2009-11-17 17:02 usplash -> /lib/init/upstart-job
-rwxr-xr-x   1 root root  2327 2009-09-19 16:03 wpa-ifupdown
-rwxr-xr-x   1 root root  1777 2008-12-04 18:44 x11-common[/FONT]

Thanks again for the help.

David

---

### Post by tashirosgt on 2009-12-17
I'm having the same problem with Ubuntu 8.04.  I thought I had everything working.  Then I turned off the "Check for Updates" box in System->Administration->Software Sources, updates tab and rebooted and the system hung -  at the login screen, as I recall.

Even if unchecking that box fixes the problem (haven't tried it yet) that would be unsatisfactory since the update process would interrupt other things.  I have not installed gnome-ppp yet. I'm just using System->Administration->Network and trying to make or break the connection by checking or unchecking the point-to-point connection.  Is that supposed to work?

How have you set the "Check For Updates"?

---

### Post by tashirosgt on 2009-12-18
I made some dubious progress.  Left the modem on while I booted (connected to the phone line).  Let it dial as the machine came up.  Went to System->Administration->Network.  Highlighted the "Point to point..." connection without checking or unchecking the box.  Picked the "Properties Button", went to the "Options" tab.  Unchecked all 3 of those boxes.  Hit the "OK" button.  Got out of the GUI.  Came back in and made sure those 3 boxes stayed unchecked.  

I did install gnome-ppp by the Wired Connection, which I had gotten to work before this modem adventure.  pppconfig was already installed.  I ran it and did configuration.  Then I ran gnome-ppp and setup the dialup connection.   Rebooted the machine.  The modem still dialed.  The connection it made was useless, the browser saw nothing.    I used "sudo ifconfig ppp0 down" and "sudo ifconfig eth0 down".  The modem lights stayed lit indicating it was still busy.  I powered it off and then on.  Then I was able to use gnome-ppp to get a usable connection. ( I had to re-enter the username etc. that is on the first screen since apparently this gets lost if you fail to connect.)

A paranoid modem user would suspect that Ubuntu is never really tested in a dialup environment!   In fact, does the distribution assume that you will make some connection as soon as you boot?   Where is the option NOT to initiate a connection?    I don't even know how to stop eth0 from coming up.

---

