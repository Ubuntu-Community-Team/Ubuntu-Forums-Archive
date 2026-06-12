---
title: "DHCP lease problem"
date: 2006-02-20
forum: Networking &amp; Wireless
---

### Post by fm1234 on 2006-02-20
Hi,

the dhclient gets an IP from my router which is configured for infinite lease time. However, each time I reboot the machine it gets a different IP. Now, I'm sure this is not the router because it works fine with a Windows amchine and it worked fine with some versions of SUSE and/or Mandrake.

In addition, I see that /var/lib/dhcp3/dhclient.leases is empty. This file is owned by root and permissions are 644. I assume dhclient is run as root, so it should be ok. From the man pages I can't really figure out why the lease is not kept between reboots.

Any clues?

TIA,
Fernando

---

### Post by cwaldbieser on 2006-02-20
[QUOTE=fm1234]Hi,

the dhclient gets an IP from my router which is configured for infinite lease time. However, each time I reboot the machine it gets a different IP. Now, I'm sure this is not the router because it works fine with a Windows amchine and it worked fine with some versions of SUSE and/or Mandrake.

In addition, I see that /var/lib/dhcp3/dhclient.leases is empty. This file is owned by root and permissions are 644. I assume dhclient is run as root, so it should be ok. From the man pages I can't really figure out why the lease is not kept between reboots.

Any clues?

TIA,
Fernando[/QUOTE]

```

$ man 5 dhclient.conf

```
Has something to say about the "reboot" configuration setting that may or may not be applicable to your situation.

---

### Post by fm1234 on 2006-02-21
Thanks for the reply cwaldbieser. I've increased reboot parameter from 10s to 60s without any difference.

In the meanwhile I found out that dhclient3 does not use the default directory to store dhclient.leases but rather uses /var/run. So, I've one lease from my router and I can't figure out nothing wrong. dhcp-lease-time is -1 which I assume means "forever". The options renew, rebind, expire seem fine.

What am I missing??

lease {
  interface "eth0";
  fixed-address 190.165.5.104;
  option subnet-mask 255.255.255.0;
  option routers 190.165.5.1;
  option dhcp-lease-time -1;
  option dhcp-message-type 5;
  option domain-name-servers 190.165.5.1,194.159.73.137;
  option dhcp-server-identifier 190.165.5.1;
  option domain-name "cmartins.demon.nl";
  renew 2 2038/1/19 03:14:07;
  rebind 2 2038/1/19 03:14:07;
  expire 2 2038/1/19 03:14:07;
}

---

