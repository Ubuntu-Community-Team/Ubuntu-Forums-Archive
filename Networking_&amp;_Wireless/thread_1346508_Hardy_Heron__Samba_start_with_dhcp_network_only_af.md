---
title: "Hardy Heron / Samba start with dhcp network only after restart service"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by TotoleHero on 2009-12-05
Hello, 

I put this information for all ubuntu hardy heron users :


If vou want to share something with samba and you have your network interface in dhcp mode you must force to restart the samba service after dhcp allocation.

My source of resolution is this message : [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/125687](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/125687)

I wrote script in /etc/network/if-up.d/ wich force samba to restart after the if-up of all interfaces

file : /etc/network/if-up.d/samba
--------------------------------------------------
#!/bin/sh

# Don't care about loopback
if [ "$IFACE" = "lo" ]; then
  exit 0
fi

/etc/init.d/samba restart
---------------------------------------------------

With this script samba start properly at boot time.

---

