---
title: "getting https traffic to pass through bridge"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by jimp180 on 2006-07-12
here is my setup I have a functioning wired network. I just got a laptop and want to connect to the internet to check email and browse the web. I had a wireless pci card sitting in the drawer that came with the mother board of my desktop pc. it has a RT2500 chip so I should be in good shape. I build a Ubuntu 6.06 server, apt-get wireless-tools and bridge-utils and then find this little script and modify it a bit 
```
 /bin/bash
# Copyright (c) 2000 Uwe Böhme.  All rights reserved.
#
# Author: Uwe Böhme <uwe@bnhof.de>, 2000
#
#
# /sbin/init.d/bridge
#

#. /etc/rc.config

return=$rc_done
case "$1" in

    start)
        echo "Starting service bridge br0"
        brctl addbr br0  ||  return=$rc_failed
        brctl setbridgeprio br0 0 || return=$rc_failed
        brctl addif br0 eth0  ||  return=$rc_failed
        brctl addif br0 ra0  ||  return=$rc_failed
        iwconfig ra0 essid "Pattitude"  ||  return=$rc_failed
	iwconfig ra0 mode "Ad-Hoc"  ||  return=$rc_failed
	iwconfig ra0 key restricted "MY284a2WEP382c53KEY14d939b"  ||  return=$rc_failed
	ifconfig eth0 0.0.0.0  ||  return=$rc_failed
        ifconfig ra0 0.0.0.0  ||  return=$rc_failed
        ifconfig br0 192.168.2.2 netmask 255.255.255.0  ||  return=$rc_failed
        brctl sethello br0 1  ||  return=$rc_failed
        brctl setmaxage br0 4  ||  return=$rc_failed
        brctl setfd br0 4  ||  return=$rc_failed

        echo -e "\t Setting Route..."
        route add default gw 192.168.2.1 || return=$rc_failed

        echo -e "$return"
        ;;

    stop)
        echo "Shutting down service bridge mueb"
        ifconfig ra0 down    ||  return=$rc_failed
        ifconfig eth0 down    ||  return=$rc_failed
        ifconfig br0 down     ||  return=$rc_failed
        brctl delif br0 ra0  ||  return=$rc_failed
        brctl delif br0 eth0  ||  return=$rc_failed
        brctl delbr br0  ||  return=$rc_failed
        rmmod bridge || return=$rc_failed

        echo -e "$return"
        ;;

    status)
        ifconfig br0
        brctl show br0
        ;;

    restart)
        $0 stop && $0 start || return=$rc_failed
        ;;

    *)
        echo "Usage: $0 {start|stop|status|restart}"
        exit 1
esac

test "$return" = "$rc_done" || exit 1
exit 0

```
and whalla! I have a transparent bridge from my dhcp/dns server to my wireless laptop. this all works great (although I never managed to get the wpa stuff working on this card) Only one major problem, I can't access any secure sites (https) from my laptop??? It just doesn't make sense for a transparent bridge that understands nothing about protocols to be doing this, is there someone out there that can tell me whats going on here?

Thanks

---

