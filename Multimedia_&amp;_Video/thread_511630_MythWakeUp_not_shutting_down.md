---
title: "MythWakeUp not shutting down"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by lerrup on 2007-07-28
I have a combined backend/frontend which I am trying to make shutdown as per the community docs to save power.

The instructions work when I start mythbackend as sudo but not if it is started as a daemon.

This is clearly a permission problem but I can't work it out.

My sudoers file is below if that helps.

Thanks.


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/Myth$

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

michael ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

mythtv ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

---

### Post by lerrup on 2007-07-28
*bump*

I would really appreciate some advice on this....

---

