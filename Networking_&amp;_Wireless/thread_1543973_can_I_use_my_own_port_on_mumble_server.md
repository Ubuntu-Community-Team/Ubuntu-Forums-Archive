---
title: "can I use my own port on mumble server?"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by hurtstotalktoyou on 2010-08-01
I'm trying to set up my own mumble server, but I don't want to use the default port 64738, for security reasons.  I've tried changing the lines:

```
# Port to bind TCP and UDP sockets to
port=64738
```

in the /etc/mumble-server.ini file to a port of my own choosing.  However, it won't work unless I use port 64738.  Is there anything I can do about this?  Do I perhaps need to change something in ice (whatever that is)?

Thanks in advance!

---

### Post by kiltach on 2010-08-15
Hey,

how is it failing?

try running with the -fg flag so you can see how its failing.
also make sure you are running with -ini so that you are actually using the ini file you edited.

murmurd -fg -ini /etc/mumble-server.ini.  Depending on how you're set up you may have to sudo.

I'm just setting up murmurd myself now and my ports keep getting tied up and then never released.  Its irritating.

netstat -antp shows among other things..

tcp6       0      0 :::64739                :::*                    LISTEN      -

---

