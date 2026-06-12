---
title: "hardware requirements - samba"
date: 2006-03-02
forum: Networking &amp; Wireless
---

### Post by joshlaf on 2006-03-02
I am running Linux on my old Dell Dimension XPS T600r.  The machine has 128MB, Pentium III 600Mhz, 100Mhz system bus.  Bought a Linksys
 10/100 network card for it and am running Samba and using the machine as a file server.  I have a newer machine running Windows XP Pro attached to it through a wireless router.

Everything appears to work great except for copying over larger files around 300MB+.  My problem is repeatable trying to copy over the same .avi files.

Windows gives me an error message that there is a CRC error and the transfer stops.  I checked the samba log log.smbd and find the following message:

lib/util_sock.c:get_peer_addr(1150)
getpeername failed.  Error was transport endpoint is not connected

Samba version 3.0.14a-ubuntu

To further diagnose I watched the Ubuntu System Monitor while a transfer was occuring and I found that after about 10-15 seconds of the transfer the CPU peaks at 100% use a lot and then the error ocurres.

What are the hardware requirements for running Samba on Ubuntu as a file server? Could this be the problem or is something simply not set up correctly?

Help

Josh

---

### Post by mips on 2006-03-03
Are you using the version of Samba from the repositories ? If yes try a later version from sourceforge.

---

