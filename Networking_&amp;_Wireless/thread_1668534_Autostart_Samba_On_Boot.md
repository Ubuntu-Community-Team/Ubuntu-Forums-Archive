---
title: "Autostart Samba On Boot"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by Muhnamana on 2011-01-16
How can I autostart samba on boot? I always need to open the terminal and type in sudo service smbd start

Anyone know how to autostart this?

---

### Post by adamluck on 2011-02-02
I've been having this problem too on my Ubuntu 10.10 server, so what I did is Google searched for a possible solution and came up with modifying the /etc/rc.local file to "restart" samba at boot time.  This is what my current file looks like:

> 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/etc/init.d/smbd restart

exit 0
So far it's working fine for me.

---

### Post by Orbital_sFear on 2011-03-31
That method will work, but its not very clean.

In my ubuntu 10.10 install, there is a file /etc/init/smbd.conf

That is where smbd is started from, here's the contents of the file:

```

description "SMB/CIFS File Server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

start on local-filesystems
stop on runlevel [!2345]

respawn

pre-start script
  RUN_MODE="daemons"

  [ -r /etc/default/samba ] && . /etc/default/samba

  [ "$RUN_MODE" = inetd ] && { stop; exit 0; }

  install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -F

```

I hope this helps.

-Orbital

---

### Post by boldford on 2011-04-01
Would that be the same in 10.04?

---

