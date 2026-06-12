---
title: "Inconsistent dhcp leases with multiple interfaces in dhclient.conf"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by Boolet on 2010-03-17
Hello all,

I have two ethernet interfaces on two different networks eth0 and eth1 (with DHCP server on each).

I would not take into account the DNS indicated by one DHCP server on eth1 (option *peerdns=no* in RPM distributions). Therefore I separate my network interfaces in */etc/dhcp3/dhclient.conf* with the declaration *interface "name" {}* and remove the *request domain-name-servers* declaration in eth1.

It works, but the two leases files */var/lib/dhcp3/dhclient.ethX.lease*s are inconsistent. They contains both eth0 and eth1 leases ! This is not the expected behavior and this raises problems: DHCPREQUEST are too much frequent.

Tested in Ubuntu 9.10 and reproduced in Ubuntu 10.04 (alpha3)

Am I wrong somewhere?

Here's some files:
*/etc/dhcp3/dhclient.conf* :
```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

# with domain-name-servers
interface "eth0"{
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
        script  "/sbin/dhclient-script";
}

# without domain-name-servers
interface "eth1"{
request subnet-mask, broadcast-address, time-offset, routers,
    host-name, ntp-servers;
        script  "/sbin/dhclient-script";
}

timeout 10;
initial-interval 2;
```*/var/lib/dhcp3/dhclient.eth0.leases* :
```
lease {
  interface "eth1";
  fixed-address 192.168.10.239;
  filename "/tftpboot/revoboot/bin/revoboot.pxe";
  option subnet-mask 255.255.255.0;
  option routers 192.168.10.254;
  option dhcp-lease-time 600;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.10.254;
  option ntp-servers 192.168.10.254;
  renew 3 2010/02/24 10:16:22;
  rebind 3 2010/02/24 10:20:57;
  expire 3 2010/02/24 10:22:12;
}
lease {
  interface "eth0";
  fixed-address 192.168.0.237;
  filename "/tftpboot/revoboot/bin/revoboot.pxe";
  option subnet-mask 255.255.255.0;
  option routers 192.168.0.254;
  option dhcp-lease-time 600;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.0.254;
  option dhcp-server-identifier 192.168.0.254;
  option ntp-servers 192.168.0.254;
  option domain-name "paris";
  renew 3 2010/02/24 10:20:21;
  rebind 3 2010/02/24 10:24:37;
  expire 3 2010/02/24 10:25:52;
}
lease {
  interface "eth1";
  fixed-address 192.168.10.239;
  filename "/tftpboot/revoboot/bin/revoboot.pxe";
  option subnet-mask 255.255.255.0;
  option routers 192.168.10.254;
  option dhcp-lease-time 600;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.10.254;
  option ntp-servers 192.168.10.254;
  renew 3 2010/02/24 10:20:08;
  rebind 3 2010/02/24 10:25:07;
  expire 3 2010/02/24 10:26:22;
}
```*/var/lib/dhcp3/dhclient.eth1.leases* :
```
lease {
  interface "eth0";
  fixed-address 192.168.0.237;
  filename "/tftpboot/revoboot/bin/revoboot.pxe";
  option subnet-mask 255.255.255.0;
  option routers 192.168.0.254;
  option dhcp-lease-time 600;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.0.254;
  option dhcp-server-identifier 192.168.0.254;
  option ntp-servers 192.168.0.254;
  option domain-name "paris";
  renew 3 2010/02/24 10:15:52;
  rebind 3 2010/02/24 10:20:27;
  expire 3 2010/02/24 10:21:42;
}
lease {
  interface "eth1";
  fixed-address 192.168.10.239;
  filename "/tftpboot/revoboot/bin/revoboot.pxe";
  option subnet-mask 255.255.255.0;
  option routers 192.168.10.254;
  option dhcp-lease-time 600;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.10.254;
  option ntp-servers 192.168.10.254;
  renew 3 2010/02/24 10:16:08;
  rebind 3 2010/02/24 10:20:37;
  expire 3 2010/02/24 10:21:52;
}
lease {
  interface "eth1";
  fixed-address 192.168.10.239;
  filename "/tftpboot/revoboot/bin/revoboot.pxe";
  option subnet-mask 255.255.255.0;
  option routers 192.168.0.254;
  option dhcp-lease-time 600;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.10.254;
  option ntp-servers 192.168.10.254;
  renew 3 2010/02/24 10:21:02;
  rebind 3 2010/02/24 10:24:53;
  expire 3 2010/02/24 10:26:08;
}
```One hour of ```
cat /var/log/syslog | grep DHCPREQUEST
``` shows :
```
Feb 24 11:00:12 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:00:14 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:00:24 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:00:25 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:00:34 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:00:44 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:00:47 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:00:54 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:00:55 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:01:05 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:01:06 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:01:15 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:01:20 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:01:29 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:01:34 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:02:37 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:02:48 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:02:54 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:03:08 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:04:20 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:05:40 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:06:15 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:06:52 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:07:06 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:07:24 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:07:27 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:07:33 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:10:18 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:10:23 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:10:31 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:10:39 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:10:45 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:10:55 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:11:03 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:11:12 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:11:14 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:11:23 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:11:24 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:11:37 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:11:42 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:11:52 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:11:58 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:12:12 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:12:19 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:14:29 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:15:52 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:15:52 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:15:56 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:16:05 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:16:08 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:16:14 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:16:22 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:16:35 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:16:47 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:17:07 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:20:08 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:20:21 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:20:33 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:20:41 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:20:42 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:20:48 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:20:56 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:21:02 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:21:02 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:21:08 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:21:13 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:21:25 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:21:27 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:21:41 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:21:49 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:21:54 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:21:58 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:24:15 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:24:19 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:24:34 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:24:42 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:25:32 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:25:45 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:26:04 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:26:17 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:28:24 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:28:32 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:30:24 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:30:33 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:30:49 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:30:51 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:30:58 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:31:01 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:31:09 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:31:16 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:31:20 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:31:36 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:31:38 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:31:53 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:31:56 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:32:07 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:32:09 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:33:02 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:33:03 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:34:32 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:34:53 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:34:54 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:35:11 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:35:54 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:36:12 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:36:16 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:36:20 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:37:36 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:37:39 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:39:00 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:39:02 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:39:21 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:41:04 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:41:08 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:41:15 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:41:19 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:41:29 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:41:36 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:41:38 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:41:43 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:41:47 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:41:57 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:42:00 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:42:04 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:42:12 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:42:18 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:42:19 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:42:37 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:42:58 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:43:02 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:43:18 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:45:03 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:46:29 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:46:34 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:47:14 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:47:32 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:47:35 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:50:29 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:50:39 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:51:12 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:51:15 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:51:23 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:51:27 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:51:35 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:51:39 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:51:52 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:51:56 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:52:08 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:52:08 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:52:16 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:52:31 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:52:31 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:52:33 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:54:50 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:54:51 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:55:02 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:55:17 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:56:26 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:56:32 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:56:40 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:56:42 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 255.255.255.255 port 67
Feb 24 11:56:48 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:56:55 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
Feb 24 11:58:50 ubuntu-9 dhclient: DHCPREQUEST of 192.168.10.239 on eth1 to 192.168.0.254 port 67
Feb 24 11:59:00 ubuntu-9 dhclient: DHCPREQUEST of 192.168.0.237 on eth0 to 192.168.0.254 port 67
```

---

### Post by Boolet on 2010-03-18
I forgot to mention that I removed NetwokManager.

---

### Post by Boolet on 2010-03-22
Hello.

Nobody has any idea ? :(

---

### Post by idallen on 2012-10-23
I'm having a similar problem with a machine with two dhcp interfaces, call them br0 and br1, one of which (br1) has an entry in the dhclient.conf file to omit DNS servers.

Each interface starts up its own dhclient instance (Ubuntu /etc/network/interfaces e.g. "iface br0 inet dhcp"), and yet the leases file for the br0 instance contains leases for both br0 and br1 interfaces, and the br1 instance broadcasts DHCPDISCOVER requests out br1 that are answered by the br1 DHCP server DHCPOFFER but that are ignored by dhclient.  Multiple DHCPDISCOVER eventually time out.

I think the problem is that if you mention any interface names in dhclient.conf, those interface names are *added* to the names mentioned on the command line.  So the dhclient instance that supposedly starts up "only" on br0 is actually starting up on br0 *and* br1, because br0 is on the command line and "br1" is in the dhclient.conf file.

What we want, is for the interfaces specified on the command line to be the *only* interfaces on which that dhclient listens and responds, but that's not how dhclient actually works.  It listens to the interfaces on the command line *and* any interfaces specified in the dhclient.conf file.  Not good.

I haven't figured out a work-around yet.

---

### Post by idallen on 2012-10-23
Okay, here's my work-around for the dhclient problem.

1. In your /etc/network/interfaces file, leave exactly one of the two DHCP interfaces as dhcp and change the all other ones to "manual".  Only one interface should be configured as dhcp.  In the stock dhclient.conf file (used by the one remaining "dhcp" interface), either remove all references to other interfaces, or make sure all those interface names match this interface.  Don't have any eth1 interface stanzas if it's eth0 that is the "dhcp" configured interface!  Everything in that stock file must either not refer to any interfaces, or it must refer to this interface.

2. Configure *all* the other DHCP interfaces as "manual" and put in explicit dhclient lines for every one of them.  Those explicit dhclient lines must use different configuration files that specify the options you need for each of those interfaces.  Example:

    up dhclient3 -e IF_METRIC=$IF_METRIC -cf /etc/dhcp/dhclient.$IFACE.conf -pf /var/run/dhclient.$IFACE.pid -lf /var/lib/dhcp3/dhclient.$IFACE.leases $IFACE

    down dhclient3 -r -cf /etc/dhcp/dhclient.$IFACE.conf -pf /var/run/dhclient.$IFACE.pid -lf /var/lib/dhcp3/dhclient.$IFACE.leases $IFACE

Now, the "dhcp" interface has its own configuration file (the stock one) that only listens on that interface, and each of the "manual" interfaces starts its own dhclient that has its own private config file that means it, too listens only on that one interface.  All dhclient processes deal with ohnly one interface.

In my set-up, I moved out my br1 special interface configuration from the stock dhclient.conf file into dhclient.br1.conf.  My dhclient.conf file was then an unmodified stock file, and I use it for my "dhcp" interface on br0.  I use a "manual" interface, with my special config file, for "br1".

---

