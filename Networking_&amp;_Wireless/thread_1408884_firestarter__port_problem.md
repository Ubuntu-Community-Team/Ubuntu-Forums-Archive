---
title: "firestarter / port problem"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by kouter on 2010-02-16
I've noticed lately that my server is really biting it on torrents, usually > 20KB/s, so re-checked my ports to ensure it wasn't a matter of blocked or improperly forwarded ports.  canyouseeme is telling me the same thing gnome's network tools port scan is, not all my ports are open.

As it stands now, I have my server behind a router (forwarding is correct on router), and my server's running a LAMP, which is working so far for HTTP, HTTPS, SSH, and IPP (80 443 22, 631 open) but not for torrents on any range (at least for the full range).

Also tried an iptables route..
iptables -A INPUT -p tcp --destination-port 6881:6999 -j ACCEPT[FONT=monospace]
[/FONT]iptables -A OUTPUT -p tcp --source-port 6881:6999 -j ACCEPT

Screenshot to further clarify - [IMG]https://badkarma.homelinux.com/web/port.jpeg[/IMG]

Any ideas?

---

### Post by superprash2003 on 2010-02-17
is your server running the server version or desktop version? make sure the torrent client is OPEN when scanning for open ports

---

### Post by kouter on 2010-02-17
running server kernel and torrenting through torrentflux using bittornado.

rebooted, and got a different port open, 6959 closed now, 6901 open.

---

### Post by kouter on 2010-02-17
this all seems to generate from a glitch in bittornado's capability to detect maximum DL speed when it is configured to 0.  Resetting the max download option to some arbitrary number (1024KB/s for me seems to be my max) results in much faster torrenting.

Hope this helps someone, because I've been searching for a while and just now tried this.

---

