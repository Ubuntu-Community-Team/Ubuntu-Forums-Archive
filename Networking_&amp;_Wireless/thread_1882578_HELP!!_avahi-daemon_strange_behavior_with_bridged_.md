---
title: "HELP!! avahi-daemon strange behavior with bridged ethernet"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by simingma on 2011-11-17
Dear all,
I am exhausted after googling for several hours.

My goal is to host AirPrint on a 10.04 Server. playing with avahi-daemon and so far everything worked perfectly - can print from Mac, iPhone with no problem.

Only after the reboot other devices no longer see the printer. But if I ssh back and do something like "service avahi-daemon restart", or even do open and close the avahi service file in /etc/avahi/service/, the printer will instant come back.

I tried to add a line to restart the daemon at boot in /etc/rc.local but didn't make any difference. At moment it only works if I login the system and do it manually.

After a while I found if use the default config for /etc/network/interface everything works fine, and it breaks when I use my bridged config with br0 (for OpenVPN).

Any idea how to make it work at boot time with bridged ethernet?

Many thanks,
Mark


Bridged ethernet config:
```

auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet manual

auto br0
iface br0 inet dhcp
pre-up openvpn --mktun --dev tap0
bridge_ports eth0 tap0

```

avahi-daemon config
```

use-ipv4=yes
use-ipv6=no

enable-wide-area=yes

rlimit-core=0
rlimit-data=4194304
rlimit-fsize=0
rlimit-nofile=300
rlimit-stack=4194304
rlimit-nproc=3

```

cat /var/log/daemon.log | grep avahi

At boot:
```

Nov 18 02:12:56 msma-mpc1 avahi-daemon[584]: Found user 'avahi' (UID 107) and group 'avahi' (GID 116).
Nov 18 02:12:56 msma-mpc1 avahi-daemon[584]: Successfully dropped root privileges.
Nov 18 02:12:56 msma-mpc1 avahi-daemon[584]: avahi-daemon 0.6.25 starting up.
Nov 18 02:12:56 msma-mpc1 avahi-daemon[584]: Successfully called chroot().
Nov 18 02:12:56 msma-mpc1 avahi-daemon[584]: Successfully dropped remaining capabilities.
Nov 18 02:12:56 msma-mpc1 avahi-daemon[584]: Loading service file /services/MF8050.service.
Nov 18 02:12:56 msma-mpc1 avahi-daemon[584]: Network interface enumeration completed.
Nov 18 02:12:56 msma-mpc1 avahi-daemon[584]: Registering new address record for fe80::214:bff:fe23:54f on br0.*.
Nov 18 02:12:56 msma-mpc1 avahi-daemon[584]: Server startup complete. Host name is msma-mpc1.local. Local service cookie is 2508948376.
Nov 18 02:12:56 msma-mpc1 avahi-daemon[584]: Service "Canon MF8050 AirPrint" (/services/MF8050.service) successfully established.
Nov 18 02:12:56 msma-mpc1 avahi-daemon[584]: Registering HINFO record with values 'I586'/'LINUX'.
Nov 18 02:13:10 msma-mpc1 avahi-daemon[584]: Joining mDNS multicast group on interface br0.IPv4 with address 192.168.1.2.
Nov 18 02:13:10 msma-mpc1 avahi-daemon[584]: New relevant interface br0.IPv4 for mDNS.
Nov 18 02:13:10 msma-mpc1 avahi-daemon[584]: Registering new address record for 192.168.1.2 on br0.IPv4.

```

After manual restart:
```

Nov 18 02:14:03 msma-mpc1 avahi-daemon[584]: Got SIGTERM, quitting.
Nov 18 02:14:03 msma-mpc1 avahi-daemon[584]: Leaving mDNS multicast group on interface br0.IPv4 with address 192.168.1.2.
Nov 18 02:14:03 msma-mpc1 init: avahi-daemon main process (584) terminated with status 255
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: Found user 'avahi' (UID 107) and group 'avahi' (GID 116).
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: Successfully dropped root privileges.
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: avahi-daemon 0.6.25 starting up.
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: Successfully called chroot().
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: Successfully dropped remaining capabilities.
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: Loading service file /services/MF8050.service.
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: Joining mDNS multicast group on interface br0.IPv4 with address 192.168.1.2.
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: New relevant interface br0.IPv4 for mDNS.
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: Network interface enumeration completed.
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: Registering new address record for fe80::214:bff:fe23:54f on br0.*.
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: Registering new address record for 192.168.1.2 on br0.IPv4.
Nov 18 02:14:03 msma-mpc1 avahi-daemon[1105]: Registering HINFO record with values 'I586'/'LINUX'.
Nov 18 02:14:04 msma-mpc1 avahi-daemon[1105]: Server startup complete. Host name is msma-mpc1.local. Local service cookie is 820997664.
Nov 18 02:14:05 msma-mpc1 avahi-daemon[1105]: Service "Canon MF8050 AirPrint" (/services/MF8050.service) successfully established.

```

---

