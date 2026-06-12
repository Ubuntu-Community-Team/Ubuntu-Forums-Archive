---
title: "DHCP used to work, but doesn't after installing ltsp-server-standalone"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by speedkreature on 2009-05-21
Trying to troubleshoot a tftp issue I was following information in >> [this thread]("http://ubuntuforums.org/showthread.php?t=737335") <<, and installed ltsp-server-standalone using aptitude.

My DHCP server was working over the last 3 days and immediately following the installation of this package, it does not.  I'm guessing I misunderstood something in that thread.

My end goal is to get a remote installation server going for Ubuntu, but a thin client install is fine too (and might actually serve my purposes better).  I haven't yet been able to determine why starting this daemon fails.

```


speedkreature@49UJJITW2:~$ sudo /etc/init.d/dhcp3-server start
 * Starting DHCP server dhcpd3                                                  
                                                                         [fail]
 * check syslog for diagnostics.
speedkreature@49UJJITW2:~$ tail /var/log/syslog
==> /var/log/syslog <==
May 21 17:31:47 49UJJITW2 dhcpd: Wrote 0 leases to leases file.
May 21 17:31:47 49UJJITW2 dhcpd: 
May 21 17:31:47 49UJJITW2 dhcpd: No subnet declaration for eth1 (192.168.49.110).
May 21 17:31:47 49UJJITW2 dhcpd: ** Ignoring requests on eth1.  If this is not what
May 21 17:31:47 49UJJITW2 dhcpd:    you want, please write a subnet declaration
May 21 17:31:47 49UJJITW2 dhcpd:    in your dhcpd.conf file for the network segment
May 21 17:31:47 49UJJITW2 dhcpd:    to which interface eth1 is attached. **
May 21 17:31:47 49UJJITW2 dhcpd: 
May 21 17:31:47 49UJJITW2 dhcpd: 
May 21 17:31:47 49UJJITW2 dhcpd: Not configured to listen on any interfaces!

```The contents of /etc/dhcp3/dhcpd.conf follows
```

# Sample /etc/dhcpd.conf
# (add your comments here) 
default-lease-time 600;
max-lease-time 691200;
allow booting;
allow bootp;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.49.255;
option routers 192.168.49.1;
option domain-name-servers 172.22.60.54, 172.22.60.51;
option domain-name "--OMITTED--.com";
option netbios-name-servers 172.22.60.51;

subnet 192.168.49.0 netmask 255.255.255.0 {
range 192.168.49.200 192.168.49.253;
#range 192.168.1.150 192.168.1.200;
filename "/tftpboot/pxelinux.0";
option root-path "/var/lib";
}
#next-server 192.168.49.110;


```

---

### Post by speedkreature on 2009-05-22
Anyone?  Did I do something incredibly stupid or does no one who has come across this thread have an idea about what's wrong?  Perhaps I should have backed up my dhcpd.conf, removed dhcp3-server, then installed ltsp-server-standalone.  In fact, I think I'll try that now...

---

### Post by bab1 on 2009-05-22
```
May 21 17:31:47 49UJJITW2 dhcpd: [COLOR="Red"]No subnet declaration for[/COLOR] eth1 (192.168.49.110).
May 21 17:31:47 49UJJITW2 dhcpd: ** Ignoring requests on eth1.  If this is not what

```

Is this the IP address of the server?  How have you configured eth1?

---

### Post by speedkreature on 2009-05-22
@bab1:
Yeah, 192.168.49.110 is the IP of the server.  eth1 is one of 2 ethernet NICs.  eth0 is disconnected.  eth1 is set to a static address via network-manager (this is an Ubuntu workstation).
I hope I answered the question as you intended it.

---

### Post by wirelessmonkey on 2009-05-22
Something is wrong with the configuration on eth1....
Can you post the output of:```

cat /etc/network/interfaces
ifconfig eth1
ifconfig eth0

```

---

### Post by bab1 on 2009-05-23
> **speedkreature said:**
> @bab1:
Yeah, 192.168.49.110 is the IP of the server.  eth1 is one of 2 ethernet NICs.  eth0 is disconnected.  eth1 is set to a static address via network-manager (this is an Ubuntu workstation).
I hope I answered the question as you intended it.

The message says that you have not configured a subnet mask for that IP address.  For the IP range you have set I would assume it would be 255.255.255.0

Look fo a spot in the network manager settings.

---

