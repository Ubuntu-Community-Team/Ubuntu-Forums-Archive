---
title: "waiting for network configuration"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by Robert Finley on 2013-01-15
Ubuntu 12.04, cli only, on an old machine

I swear, it was working. But now, on boot I get "waiting for network configuration" for a while, then it says "waiting an additional 60 seconds for network configuration".  When the machine finishes booting, I have no network. Cannot ping other machines by IP address.

/etc/networking/interfaces

# The loopback network interface

 auto lo
 iface lo inet loopback  

# The primary network interface

 auto eth0
 iface eth0 inet dhcp

/etc/hosts/

127.0.0.1    localhost 
192.168.1.115   Desktop-3  

# The following lines are desirable for IPv6 capable hosts 
::1    ip6-localhost ip6-loopback 
fe00::0   ip6-localnet 
ff00::0   ip6-mcastprefix 
ff02::1   ip6-allnodes 
ff02::2   ip6-allrouters


I found an older bug that sounded similar and the suggested fix was

mkdir -p /run /run/lock
    rm -rf /var/run /var/lock
    ln -s /run /var
    ln -s /run/lock /var
    reboot

This solution did not work.

---

### Post by Robert Finley on 2013-01-15
Bad cable connection....

---

