---
title: "Losing DNS periodically &amp; /var/lib/dhcp3/dhclient.eth0.leases: Permission denied"
date: 2006-03-31
forum: Networking &amp; Wireless
---

### Post by droazen on 2006-03-31
Hi,

I find that after several hours of being online, I inevitably lose DNS resolution. I am connecting through an ADSL modem/PPPoE, and get my DNS server addresses via DHCP. The DNS server IPs are also cached in /etc/resolv.conf. Doing "sudo poff dsl-provider" and then "sudo pon dsl-provider" restores DNS resolution for another few hours.

Looking through /var/log/syslog.* leads me to believe that the problem might be related to dhclient failing to renew its leases after a set amount of time. My log is littered with messages like this:

```

Mar 30 19:13:02 straylight dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Mar 30 19:13:02 straylight dhclient: DHCPACK from 192.168.1.1
Mar 30 19:13:02 straylight dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 30 19:13:02 straylight dhclient: bound to 192.168.1.46 -- renewal in 37541 seconds.

```

The /var/lib/dhcp3/dhclient.eth0.leases file exists, but is empty, and it's owner/group is root. The dhclient process runs as user "dhcp", so I can see why there are permissions issues going on:

```

dhcp      3118     1  0 03:45 ?        00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

```

But if dhclient is choking because of permissions issues, why does "pon" work? I don't really understand if/how pon interacts with DHCP. From the man pages it seems like pon just runs "pppd call dsl-provider", which then looks in /etc/ppp/peers/dsl-provider for the connection settings. But there is no mention of DHCP in this file.

Any thoughts? I really want to figure out how all this works haha...

---

### Post by droazen on 2006-04-02
Update:

I chown'd and chmod'd dhclient.eth0.leases so that dhclient could write to it, and I discovered that this was the kind of dhcp "information" dhclient was getting:

```

lease {
  interface "eth0";
  fixed-address 192.168.1.46;
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option dhcp-lease-time 86400;
  option dhcp-message-type 5;
  **option domain-name-servers 192.168.1.1,192.168.1.1;**
  option dhcp-server-identifier 192.168.1.1;
  option broadcast-address 255.255.255.255;
  option domain-name "myhome.westell.com";
  renew 0 2006/4/2 17:08:00;
  rebind 1 2006/4/3 03:45:35;
  expire 1 2006/4/3 06:45:35;
}

```

Haha so I never really had dhcp working in the first place! :rolleyes:  What was happening was: "pppd call dsl-provider" would run, getting the correct dns server ips from my isp (since the "usepeerdns" option was enabled in /etc/ppp/peers/dsl-provider) and writing them to /etc/resolv.conf. Then, ~10 hours later or so, dhclient would run and try to renew its lease. When it asked for a name server it would get the local address of my dsl modem (192.168.1.1). Then it would overwrite the correct dns server ips in /etc/resolv.conf with 192.168.1.1 - causing me to lose dns resolution until I re-ran pppd via the "pon" script.

The solution was to enable the "prepend domain-name-servers" in /etc/dhcp3/dhclient.conf, and hardcode my dns server addresses there. Now when dhclient runs, it *still* writes 192.168.1.1 to /etc/resolv.conf, but it also writes the correct addresses before it.

---

