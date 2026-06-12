---
title: "System hang, any way to debug ?"
date: 2008-07-17
forum: Mythbuntu
---

### Post by erland on 2008-07-17
I had a complete system hang yesterday in my Mythbuntu 8.04 box. Is there some log files I should look at to check the reason for the hang ?

The machine locked completely, the display locked and showed the MythTV main menu where it was standing before before the hang. The computer didn't answer to keyboard or IR commands and it was no longer available on the network and the harddrive light showed that the harddrive wasn't accessed. The only solution to get back to a working situation was to do a hard reset using the power button.

After the machine got up again I tried to look in the log but it just looked like I didn't get any more log entries when the machine hang.

The hang happend at 06:36, here are some log files:

/var/log/mythtv/mythbackend.log
```

2008-07-16 06:33:23.334 Reschedule requested for id -1.
2008-07-16 06:33:36.754 Scheduled 490 items in 13.4 = 1.07 match + 12.34 place
2008-07-16 06:33:36.821 scheduler: Scheduled items: Scheduled 490 items in 13.4 = 1.07 match + 12.34 place
2008-07-16 06:33:44.747 MainServer::HandleAnnounce Monitor
2008-07-16 06:33:45.117 adding: htpclin as a client (events: 0)
2008-07-16 06:33:45.119 MainServer::HandleAnnounce Monitor
2008-07-16 06:33:45.119 adding: htpclin as a client (events: 1)
2008-07-16 06:33:45.121 Reschedule requested for id -1.
2008-07-16 06:33:48.490 Scheduled 490 items in 3.4 = 0.61 match + 2.76 place
2008-07-16 06:33:48.500 scheduler: Scheduled items: Scheduled 490 items in 3.4 = 0.61 match + 2.76 place
2008-07-16 06:34:58.427 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
2008-07-17 01:12:56.329 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 01:12:56.511 Empty LocalHostName.

```

/var/log/syslog
```

Jul 16 06:26:57 htpclin last message repeated 2 times
Jul 16 06:27:50 htpclin last message repeated 2 times
Jul 16 06:28:42 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 16 06:30:01 htpclin /USR/SBIN/CRON[26922]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Jul 16 06:33:45 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 16 06:33:46 htpclin syslogd 1.5.0#1ubuntu1: restart.
Jul 16 06:33:56 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 16 06:34:05 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 16 06:35:40 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 17 01:12:48 htpclin syslogd 1.5.0#1ubuntu1: restart.
Jul 17 01:12:48 htpclin kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 17 01:12:48 htpclin kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Jul 17 01:12:48 htpclin kernel: Symbols match kernel version 2.6.24.

```

/var/log/messages
```

Jul 16 06:07:37 htpclin -- MARK --
Jul 16 06:27:37 htpclin -- MARK --
Jul 16 06:33:46 htpclin syslogd 1.5.0#1ubuntu1: restart.
Jul 17 01:12:48 htpclin syslogd 1.5.0#1ubuntu1: restart.
Jul 17 01:12:48 htpclin kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 17 01:12:48 htpclin kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-gen

```

/var/log/user.log
```

Jul 16 06:25:43 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 16 06:27:08 htpclin last message repeated 3 times
Jul 16 06:27:50 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 16 06:28:42 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 16 06:33:45 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 16 06:33:56 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 16 06:34:05 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 16 06:35:40 htpclin sasc-ng: [25477] [general.error] action logger 0/1 read: Buffer overflow
Jul 17 01:12:57 htpclin dhcdbd: Started up.

```

Is there any other log files which I should look in to find out what could have caused the problem ?

---

### Post by laga on 2008-07-17
Ugh, softcams. You should ask about this somewhere else.

---

### Post by superm1 on 2008-07-17
<Zinn> sasc-ng is a method to ILLEGALLY receive cable or satellite broadcasts via a fake software dvb-s/c device.  It is forbidden from being discussed in #ubuntu-mythtv, #ubuntu-mythtv-dev, #mythtv-users, and #mythtv.  If you would like to learn more about it, please refer to it's developers and keep any and all discussions about it there.

---

