---
title: "Unable to control lcdproc options on Imon VFD"
date: 2010-02-27
forum: Multimedia Software
---

### Post by das1969 on 2010-02-27
I've been trying to configure my Imon VFD in 64-bit ubuntu.

I've now gotten LCDd and lcdproc set and running when I boot by adding scripts to /etc/rc2.d/ so that lcdproc runs after LCDd.

I've also created my own daemon for ldcproc in /etc/init.d/, by copying that for LCDd and changing the following:

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/lcdproc
NAME="lcdproc"
DESC="lcdproc"
DAEMON_OPTS=" T"

The options are set to just show the time, however when lcdproc is run, the time is displayed for around 5 seconds, but then the VFD displays each of the other screens, CPU, Disk, Network etc.

I just want the VFD to show the system date and time, but will not do so whichever way I set the options. When I stop lcdproc, and then restart using the command

sudo lcdproc T

The same pattern of behaviour occurs.

---

### Post by mal205 on 2010-03-30
I had the same challenge. You need to edit "/etc/lcdproc.conf".

When lcdproc is run it will display all the screens you specify with the command PLUS all the screens marked as Active=True in lcdproc.conf. 

Just edit lcdproc.conf and change True to false for all options and only the screen specified with the command will run. Alternatively, specify the screen(s) you want in lcdproc.conf.

---

