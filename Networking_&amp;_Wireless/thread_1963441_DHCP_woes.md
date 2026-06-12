---
title: "DHCP woes"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2012-04-22
Hi all,

I am having some DHCP issues. The DHCP server on the Ubuntu box should be using a 10.10.10.X

However I am getting IP adddres in the 192.186.1.X range. 


AT the bottom I have 2 huge chucks from before an after I made some change.
I assume that the problem here is 2 DHCP servers. However they are both set to 10.10.10.X
DHCPREQUEST for 192.168.1.6 from 40:a6:d9:20:06:d2 via eth0: ignored (not authoritative)

Why is the request coming from "192.168.1.6" how did that device get that address? 

Do I have a rouge DHCP server?


```

Apr 22 11:05:29 philo dhcpd: DHCPREQUEST for 10.10.10.51 from 70:73:cb:76:bb:cb via eth0: unknown lease 10.10.10.51.
Apr 22 11:05:31 philo dhcpd: DHCPREQUEST for 192.168.1.19 from 70:73:cb:76:bb:cb via eth0: ignored (not authoritative).
Apr 22 11:05:31 philo dhcpd: DHCPDISCOVER from 70:73:cb:76:bb:cb via eth0: network 10.10.10.0/24: no free leases
Apr 22 11:05:32 philo dhcpd: DHCPREQUEST for 10.10.10.51 (10.10.10.1) from 70:73:cb:76:bb:cb via eth0: unknown lease 10.10.10.51.
Apr 22 11:08:10 philo dhcpd: DHCPREQUEST for 10.0.0.8 from 00:26:b0:42:15:41 via eth0: ignored (not authoritative).
Apr 22 11:08:11 philo dhcpd: DHCPREQUEST for 10.10.10.55 from 00:26:b0:42:15:41 via eth0: unknown lease 10.10.10.55.
Apr 22 11:08:11 philo dhcpd: DHCPDISCOVER from 00:26:b0:42:15:41 via eth0: network 10.10.10.0/24: no free leases
Apr 22 11:08:12 philo dhcpd: DHCPREQUEST for 192.168.1.29 (192.168.1.1) from 00:26:b0:42:15:41 via eth0: ignored (not authoritative).
Apr 22 11:14:29 philo kernel: [70621.004315] e100 0000:01:08.0: eth0: NIC Link is Down
Apr 22 11:14:31 philo kernel: [70623.004166] e100 0000:01:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
Apr 22 11:14:47 philo avahi-daemon[724]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::203:47ff:fef4:1dc1.
Apr 22 11:14:47 philo avahi-daemon[724]: Joining mDNS multicast group on interface eth0.IPv6 with address 2002:4659:a65:1234:203:47ff:fef4:1dc1.
Apr 22 11:14:47 philo avahi-daemon[724]: Registering new address record for 2002:4659:a65:1234:203:47ff:fef4:1dc1 on eth0.*.
Apr 22 11:14:47 philo avahi-daemon[724]: Withdrawing address record for fe80::203:47ff:fef4:1dc1 on eth0.
Apr 22 11:16:24 philo named[788]: error (network unreachable) resolving 'updateservice.sonic.comping.asp/A/IN': 2001:503:ba3e::2:30#53
Apr 22 11:16:30 philo named[788]: success resolving 'updateservice.sonic.comping.asp/A' (in '.'?) after reducing the advertised EDNS UDP packet size to 512 octets
Apr 22 11:16:30 philo avahi-daemon[724]: Registering new address record for 2002:18b5:bc3f:1234:203:47ff:fef4:1dc1 on eth0.*.
Apr 22 11:17:01 philo CRON[11925]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 22 11:17:28 philo avahi-daemon[724]: Withdrawing address record for 2002:4659:a65:1234:203:47ff:fef4:1dc1 on eth0.
Apr 22 11:20:28 philo avahi-daemon[724]: Leaving mDNS multicast group on interface eth0.IPv6 with address 2002:4659:a65:1234:203:47ff:fef4:1dc1.
Apr 22 11:20:28 philo avahi-daemon[724]: Joining mDNS multicast group on interface eth0.IPv6 with address 2002:18b5:bc3f:1234:203:47ff:fef4:1dc1.
Apr 22 11:28:46 philo dhcpd: DHCPDISCOVER from 28:ef:01:85:26:90 via eth0: network 10.10.10.0/24: no free leases
Apr 22 11:28:46 philo dhcpd: DHCPREQUEST for 192.168.1.11 (192.168.1.1) from 28:ef:01:85:26:90 via eth0: ignored (not authoritative).
Apr 22 11:43:35 philo dhcpd: DHCPREQUEST for 192.168.1.6 from 40:a6:d9:20:06:d2 via eth0: ignored (not authoritative).
Apr 22 11:48:58 philo dhcpd: DHCPREQUEST for 192.168.1.29 from 00:26:b0:42:15:41 via eth0: ignored (not authoritative).
Apr 22 11:48:58 philo dhcpd: DHCPDISCOVER from 00:26:b0:42:15:41 via eth0: network 10.10.10.0/24: no free leases
Apr 22 11:49:00 philo dhcpd: DHCPREQUEST for 10.10.10.50 (10.10.10.1) from 00:26:b0:42:15:41 via eth0: unknown lease 10.10.10.50.
Apr 22 11:49:19 philo dhcpd: DHCPREQUEST for 192.168.1.6 from 40:a6:d9:20:06:d2 via eth0: ignored (not authoritative).
Apr 22 11:50:55 philo dhcpd: DHCPREQUEST for 192.168.1.9 from 14:da:e9:2b:bf:34 via eth0: ignored (not authoritative).
Apr 22 11:55:36 philo dhcpd: DHCPDISCOVER from 44:a7:cf:91:dc:4e via eth0: network 10.10.10.0/24: no free leases
Apr 22 11:55:36 philo dhcpd: DHCPREQUEST for 192.168.1.12 (192.168.1.1) from 44:a7:cf:91:dc:4e via eth0: ignored (not authoritative).
Apr 22 11:59:40 philo dhcpd: DHCPDISCOVER from 40:a6:d9:20:06:d2 via eth0: network 10.10.10.0/24: no free leases
Apr 22 11:59:48 philo dhcpd: DHCPREQUEST for 192.168.1.6 from 40:a6:d9:20:06:d2 via eth0: ignored (not authoritative).
Apr 22 12:00:33 philo dhcpd: DHCPREQUEST for 192.168.1.17 from 4c:b1:99:bd:b2:c8 via eth0: ignored (not authoritative).
Apr 22 12:00:35 philo dhcpd: DHCPREQUEST for 10.10.10.149 from 4c:b1:99:bd:b2:c8 via eth0: unknown lease 10.10.10.149.
Apr 22 12:00:35 philo dhcpd: DHCPDISCOVER from 4c:b1:99:bd:b2:c8 via eth0: network 10.10.10.0/24: no free leases
Apr 22 12:00:36 philo dhcpd: DHCPDISCOVER from 4c:b1:99:bd:b2:c8 via eth0: network 10.10.10.0/24: no free leases
Apr 22 12:00:38 philo dhcpd: DHCPREQUEST for 10.10.10.55 (10.10.10.1) from 4c:b1:99:bd:b2:c8 via eth0: unknown lease 10.10.10.55.
Apr 22 12:01:16 philo dhcpd: DHCPREQUEST for 192.168.1.6 from 40:a6:d9:20:06:d2 via eth0: ignored (not authoritative).
Apr 22 12:01:16 philo dhcpd: DHCPDISCOVER from 40:a6:d9:20:06:d2 via eth0: network 10.10.10.0/24: no free leases
Apr 22 12:01:18 philo dhcpd: DHCPREQUEST for 10.10.10.54 (10.10.10.1) from 40:a6:d9:20:06:d2 via eth0: unknown lease 10.10.10.54.
Apr 22 12:02:05 philo dhcpd: DHCPREQUEST for 10.10.10.109 from a4:d1:d2:54:28:55 via eth0: unknown lease 10.10.10.109.
Apr 22 12:02:05 philo dhcpd: DHCPDISCOVER from a4:d1:d2:54:28:55 via eth0: network 10.10.10.0/24: no free leases
Apr 22 12:02:06 philo dhcpd: DHCPDISCOVER from a4:d1:d2:54:28:55 via eth0: network 10.10.10.0/24: no free leases
Apr 22 12:02:08 philo dhcpd: DHCPREQUEST for 10.10.10.56 (10.10.10.1) from a4:d1:d2:54:28:55 via eth0: unknown lease 10.10.10.56.
Apr 22 12:03:12 philo dhcpd: DHCPREQUEST for 192.168.1.30 from 18:34:51:38:8d:0e via eth0: ignored (not authoritative).
Apr 22 12:03:14 philo dhcpd: DHCPREQUEST for 10.10.10.34 from 18:34:51:38:8d:0e via eth0: unknown lease 10.10.10.34.
Apr 22 12:03:14 philo dhcpd: DHCPDISCOVER from 18:34:51:38:8d:0e via eth0: network 10.10.10.0/24: no free leases
Apr 22 12:03:17 philo dhcpd: DHCPREQUEST for 10.10.10.57 (10.10.10.1) from 18:34:51:38:8d:0e via eth0: unknown lease 10.10.10.57.
Apr 22 12:06:04 philo dhcpd: DHCPREQUEST for 192.168.1.15 from 70:de:e2:d4:d8:4d via eth0: ignored (not authoritative).
Apr 22 12:06:04 philo dhcpd: DHCPDISCOVER from 70:de:e2:d4:d8:4d via eth0: network 10.10.10.0/24: no free leases
Apr 22 12:06:05 philo dhcpd: DHCPDISCOVER from 70:de:e2:d4:d8:4d via eth0: network 10.10.10.0/24: no free leases
Apr 22 12:06:07 philo dhcpd: DHCPREQUEST for 10.10.10.58 (10.10.10.1) from 70:de:e2:d4:d8:4d via eth0: unknown lease 

```





```


Apr 22 08:22:42 philo dhcpd: DHCPINFORM from 192.168.1.8 via eth0: unknown subnet for client address 192.168.1.8
Apr 22 08:24:12 philo dhcpd: DHCPINFORM from 192.168.1.8 via eth0: unknown subnet for client address 192.168.1.8
Apr 22 08:27:04 philo dhcpd: DHCPREQUEST for 192.168.1.4 from 70:de:e2:d4:d8:4d via eth0: ignored (not authoritative).
Apr 22 08:27:04 philo dhcpd: DHCPDISCOVER from 70:de:e2:d4:d8:4d via eth0: network 10.10.10.0/24: no free leases
Apr 22 08:27:05 philo dhcpd: DHCPREQUEST for 192.168.1.15 (192.168.1.1) from 70:de:e2:d4:d8:4d via eth0: ignored (not authoritative).
Apr 22 08:30:44 philo dhcpd: DHCPREQUEST for 192.168.6.179 from a4:d1:d2:e4:1b:57 via eth0: ignored (not authoritative).
Apr 22 08:30:44 philo dhcpd: DHCPDISCOVER from a4:d1:d2:e4:1b:57 via eth0: network 10.10.10.0/24: no free leases
Apr 22 08:30:46 philo dhcpd: DHCPREQUEST for 192.168.1.23 (192.168.1.1) from a4:d1:d2:e4:1b:57 via eth0: ignored (not authoritative).
Apr 22 08:33:25 philo dhcpd: DHCPREQUEST for 192.168.1.23 from a4:d1:d2:e4:1b:57 via eth0: ignored (not authoritative).
Apr 22 08:34:50 philo dhcpd: DHCPREQUEST for 192.168.1.5 from 14:da:e9:2b:bf:34 via eth0: ignored (not authoritative).
Apr 22 08:34:52 philo dhcpd: DHCPDISCOVER from 14:da:e9:2b:bf:34 via eth0: network 10.10.10.0/24: no free leases
Apr 22 08:34:52 philo dhcpd: DHCPREQUEST for 192.168.1.9 (192.168.1.1) from 14:da:e9:2b:bf:34 via eth0: ignored (not authoritative).
Apr 22 08:38:44 philo dhcpd: DHCPREQUEST for 192.168.1.8 from c4:3d:c7:d5:56:90 via eth0: ignored (not authoritative).
Apr 22 08:38:50 philo dhcpd: DHCPREQUEST for 192.168.1.8 from c4:3d:c7:d5:56:90 via eth0: ignored (not authoritative).
Apr 22 08:38:56 philo dhcpd: DHCPINFORM from 192.168.1.8 via eth0: unknown subnet for client address 192.168.1.8
Apr 22 08:42:26 philo dhcpd: DHCPREQUEST for 192.168.6.102 from 14:8f:c6:df:3d:ab via eth0: ignored (not authoritative).
Apr 22 08:42:26 philo dhcpd: DHCPDISCOVER from 14:8f:c6:df:3d:ab via eth0: network 10.10.10.0/24: no free leases
Apr 22 08:42:28 philo dhcpd: DHCPREQUEST for 192.168.1.24 (192.168.1.1) from 14:8f:c6:df:3d:ab via eth0: ignored (not authoritative).
Apr 22 08:48:26 philo dhcpd: DHCPRELEASE of 192.168.1.141 from 00:25:d3:ec:46:b7 via eth0 (not found)
Apr 22 08:48:32 philo dhcpd: DHCPREQUEST for 10.10.10.62 from 00:1d:09:8c:74:ec via eth0: unknown lease 10.10.10.62.
Apr 22 08:48:33 philo dhcpd: DHCPDISCOVER from 00:1d:09:8c:74:ec via eth0: network 10.10.10.0/24: no free leases
Apr 22 08:48:34 philo dhcpd: DHCPREQUEST for 192.168.1.25 (192.168.1.1) from 00:1d:09:8c:74:ec via eth0: ignored (not authoritative).
Apr 22 08:48:41 philo dhcpd: DHCPINFORM from 192.168.1.25 via eth0: unknown subnet for client address 192.168.1.25
Apr 22 08:49:03 philo dhcpd: DHCPDISCOVER from 00:25:d3:ec:46:b7 via eth0: network 10.10.10.0/24: no free leases
Apr 22 08:49:03 philo dhcpd: DHCPDISCOVER from 00:25:d3:ec:46:b7 via eth0: network 10.10.10.0/24: no free leases
Apr 22 08:49:43 philo dhcpd: DHCPINFORM from 192.168.1.25 via eth0: unknown subnet for client address 192.168.1.25
Apr 22 08:49:54 philo dhcpd: DHCPDISCOVER from 00:25:d3:ec:46:b7 via eth0: network 10.10.10.0/24: no free leases



```

---

### Post by SeijiSensei on 2012-04-22
Do you have a firewall router somewhere on the network like between your network and the Internet?  Check to see if its DHCP server is enabled.  Addresses in 192.168.1.0/24 are pretty commonly distributed by things like Linksys and Netgear routers.

---

### Post by chili555 on 2012-04-22
I think that simply means that the system connected once upon a time to a 192.168.x.y network. A record of the lease is recorded, often in /var/lib/dhcp/dhclient-<big_long_number>-eth0.lease. When you ask for an IP address, dhclient tries all of them until it gets an IP address. Typically, the last lease recorded is the one you want, so you won't see all the failed attempts you see above.

Your syslog just suggests that there is a problem with your 10.x.x.1 DHCP servers, so dhclient looks further down the leases and fails there, too. In other words, the appearance of 192.168.x.y actually is telling you that you have a 10.x.x.1 problem. I suspect this is the real problem:> network 10.10.10.0/24: [COLOR="Red"]no free leases[/COLOR]

---

### Post by wlraider70 on 2012-04-22
I do have a linksys router on the network 10.10.10.1 It has a DHCP server. I think that the way I had it was in one of those big code groups it was enabled and in one it was not. 


as for the leases, are they referring to every number in the rage being used I think i had 100 dynamic address allocated, i certainly don't have 100 devices. Do i increase the range.

---

### Post by chili555 on 2012-04-22
> I _think_ i had 100 dynamic address allocated, Would you check? The message is suspiciously like you had five addresses allowable and this computer is asking for number six, or similar. You might also power cycle the router; that is, unplug it, open a refreshing beverage, count to 23 and plug it back in. See if you get addresses then.

---

### Post by wlraider70 on 2012-04-22
This is my dhcp.conf

The range part of the file was missing, so I added it at the top.
I'm not entirely sure about the order, but as i understand it there 100 ips allowed. 


```

range 10.10.10.100 10.10.10.200;

$}

INTERFACES="eth0"


ddns-update-style none;
log-facility local7;

subnet 10.10.10.0 netmask 255.255.255.0 {

        option routers                  10.10.10.1;
        option subnet-mask              255.255.255.0;
        option broadcast-address        10.10.10.255;
        option domain-name-servers      10.10.10.2;
        option netbios-name-servers     10.10.10.2;
        option netbios-node-type 2;
        default-lease-time 86400;
        max-lease-time 86400;

        host philo {
                hardware ethernet 00:03:47:F4:1D:C1;
                fixed-address 10.10.10.2;
        }

}

```

---

### Post by chili555 on 2012-04-22
So how about now? Do you still get this or some other message?> 
Apr 22 08:49:03 philo dhcpd: DHCPDISCOVER from 00:25:d3:ec:46:b7 via eth0: network 10.10.10.0/24: [COLOR="Red"]no free leases[/COLOR]

---

### Post by wlraider70 on 2012-04-22
I'm remoting into my network and its late so no one is there. 
I just caused this.


Apr 22 20:25:43 philo dhcpd: DHCPDISCOVER from 00:1d:09:8c:88:a1 via eth0: network 10.10.10.0/24: no free leases
Apr 22 20:25:44 philo dhcpd: DHCPREQUEST for 10.10.10.61 (10.10.10.1) from 00:1d:09:8c:88:a1 via eth0: unknown lease 10.10.10.61.

As far as I can tell the request went to the DHCP server twice. It was denyied once and made it through on the second attempt.

The PC I used to generate the request is using 10.10.10.61 as its ip. It definitely got that address from DHCP. 


Is there a file to check for my current leases?





This may or may not be relevant...

```

DHCPINFORM from 10.10.10.5 via eth0: not authoritative for subnet 10.10.10.0
 If this DHCP server is authoritative for that subnet,
 please write an `authoritative;' directive either in the
 subnet declaration or in some scope that encloses the
 subnet declaration - for example, write it at the top
 of the dhcpd.conf file.

 DHCPINFORM from 10.10.10.5 via eth0: not authoritative for subnet 10.10.10.0

```

10.10.10.5 is a static IP for a printer.
There is an authoritative statement in the dhcpd.conf, am I misunderstanding the meaning.

---

### Post by chili555 on 2012-04-22
> Is there a file to check for my current leases?Other than ifconfig and /var/lib/dhcp/, I have no more ideas. If the machine got an IP address and can ping the router, may I assume the case is solved? I believe what fixed it was the inclusion of a DHCP range:> range 10.10.10.100 10.10.10.200;I wonder why the address you got is outside the range!

I'm not aware of the significance of:> DHCPINFORM from 10.10.10.5 via eth0: not authoritative for subnet 10.10.10.0There is some interesting information here:```
man dhclient
```

---

### Post by iponeverything on 2012-04-22
```
DHCPINFORM from 10.10.10.5 via eth0: not authoritative for subnet 10.10.10.0 
```

what is the address and netmask on eth0 of the DHCP server?

---

### Post by wlraider70 on 2012-04-22
I'll have to wait till tomorrow to verify that its fixed, but things do look good. I want to see the other clients that we were having issues.

eth0 is 

10.10.10.2 
255.255.255.0

Thanks for the help thus far.

---

### Post by newbie-user on 2012-04-22
> **wlraider70 said:**
> This is my dhcp.conf

The range part of the file was missing, so I added it at the top.
I'm not entirely sure about the order, but as i understand it there 100 ips allowed. 


```

range 10.10.10.100 10.10.10.200;

$}

INTERFACES="eth0"


ddns-update-style none;
log-facility local7;

subnet 10.10.10.0 netmask 255.255.255.0 {

        option routers                  10.10.10.1;
        option subnet-mask              255.255.255.0;
        option broadcast-address        10.10.10.255;
        option domain-name-servers      10.10.10.2;
        option netbios-name-servers     10.10.10.2;
        option netbios-node-type 2;
        default-lease-time 86400;
        max-lease-time 86400;

        host philo {
                hardware ethernet 00:03:47:F4:1D:C1;
                fixed-address 10.10.10.2;
        }

}

```

The problem here is that your range statement is outside your subnet declaration. So currently, there is no allowed range for your 10.10.10.0/24 network.

---

### Post by SeijiSensei on 2012-04-22
The leases are stored in the file called [dhcpd.leases]("http://manpages.ubuntu.com/manpages/maverick/man5/dhcpd.leases.5.html"), probably under /var/lib/dhcp3/.

---

### Post by wlraider70 on 2012-04-22
FIXED IT!

I'm not exactly sure what I did. I checked my ; and } . rearranged the conf file and restarted the server, and it was all good. 

many thanks all.

---

### Post by newbie-user on 2012-04-22
> **wlraider70 said:**
> ???




```

Apr 22 21:42:16 philo dhcpd: WARNING: _Host declarations are global.  They are not limited to the scope you declared them in._
Apr 22 21:42:16 philo dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Apr 22 21:42:16 philo dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Apr 22 21:42:16 philo dhcpd: All rights reserved.
Apr 22 21:42:16 philo dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Apr 22 21:42:16 philo dhcpd: Wrote 0 deleted host decls to leases file.
Apr 22 21:42:16 philo dhcpd: Wrote 0 new dynamic host decls to leases file.
Apr 22 21:42:16 philo dhcpd: Wrote 0 leases to leases file.
Apr 22 21:48:16 philo dhcpd: DHCPDISCOVER from 00:1d:09:8c:88:a1 via eth0: network 10.10.10.0/24: no free leases
Apr 22 21:49:21  dhcpd: last message repeated 3 times
Apr 22 21:50:21  dhcpd: last message repeated 3 times
Apr 22 21:50:24 philo dhcpd: **DHCPDISCOVER from 00:1d:09:8c:88:a1 via eth0: network 10.10.10.0/24: no free leases**

```

Yes, host declarations are supposed to be global and not placed within the subnet declaration. I missed that. A basic subnet declaration should look like this, with your host declarations outside of the subnet declaration:

subnet 10.10.10.0 netmask 255.255.255.0 {
     range 10.10.10.100 10.10.10.200;
     option routers 10.10.10.1;
     option domain-name-servers [dns ip];
     }

host test1 {
     hardware address [mac address];
     fixed-address [ip address];
     }

---

