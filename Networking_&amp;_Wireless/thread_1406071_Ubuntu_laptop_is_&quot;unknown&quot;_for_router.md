---
title: "Ubuntu laptop is &quot;unknown&quot; for router"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by vanadium on 2010-02-13
Any Ubuntu system that connects to my router (Netgear Super Wireless ADSL Router DG834GT) does not acquire a host name on the network. The router reports the IP, and "unknown" as the "device name". As a consequence, the PC can only be reached over the intranet using an ip address, not using a hostname.

My mybookworld network drive, that also runs a flavour of linux, does appear to my router with the name "networkspace". This must therefore be a network configuration issue of Ubuntu.

I have a hostname set in my Ubuntu system.

```

vanadium@vanadium:~$ hostname
vanadium
vanadium@vanadium:~$ hostname -a
localhost  vanadium 
vanadium@vanadium:~$ hostname --fqdn
localhost.localdomain
vanadium@vanadium:~$ cat /etc/hosts
127.0.0.1	localhost.localdomain localhost vanadium

# The following lines are desirable for IPv6 capable hosts
<snip>

```

What could I adjust in my Ubuntu configuration such that also Ubuntu systems acquire a hostname in the router, working as a DCHP server?

---

### Post by Iowan on 2010-02-13
Look in */etc/dhcp3/dhclient.conf* for the line:```
send host-name "<hostname>";
``` Change <hostname> to the your hostname, and restart.

---

### Post by vanadium on 2010-02-14
Unfortunately, this does not change anything, even after a reboot of all systems. I tried to explore configuration differences between my network drive and Ubuntu, but the systems are different: the network drive for one thing does not have such a dhclient file.

---

### Post by Iowan on 2010-02-14
Most of my machines use only localhost (and localhost.localdomain) for 127.0.0.1. The descriptive hostname is assigned to 127.0.1.1 - although I noticed my Karmic box puts the descriptive name in both places.

---

### Post by vanadium on 2010-02-15
I guess I will have to continue work around it using reserved IP-adresses and adapted hosts files on the clients. Thanks for your input.

---

### Post by Iowan on 2010-02-15
Some DHCP servers (which also allow static leases) will let you assign a hostname. It's not as clean/easy as letting the clients pass along their own name...

---

### Post by vanadium on 2010-02-16
The curious issue is that my router receives the name from a minimal linux system on the Mybookworld, Windows millenium, but not from any Ubuntu system.

---

