---
title: "Remote / IR Fails: LIRC, Error: Failed to connect to Unix socket '/dev/lircd' eno . ."
date: 2011-10-29
forum: Mythbuntu
---

### Post by linux.rog on 2011-10-29
My Mythbuntu 11.10 install give me errors related to my IR receiver and blaster. I'm installing a Hauppauge 1600 74301 LF. I get this error:

    LIRC, Error: Failed to connect to Unix socket '/dev/lircd' eno: No such file or directory (2)

The frontend log says,

    LIRC, Error: Failed to connect to Unix socket '/dev/lircd' eno: No such file or directory (2)

I configured the remote with Myth Control Center as follows:

USB & serical support via LIRC

Enabled remote - Hauppauge TV card
Enabled IR transmitter, Command IR: Motorola Cable Box

I have a Motorola QUP 7100 series set-top box.

syslog includes this line:
mythtv kernel: [   17.899333] lirc_dev: IR Remote Control driver registered, major 250

Logs (tails) and conf files are posted at [http://](http://)[www.bronord.com/myth]("http://www.bronord.com/myth"): back- and frontend logs, syslog, dmseg, lircd.conf, hardware.conf

If I change options for IR using myth control center, corresponding changes occur in, e.g., lircd.conf but I get no combination that works and I've tried a bunch.

---

