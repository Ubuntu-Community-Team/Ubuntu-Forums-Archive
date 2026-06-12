---
title: "ipv6+dhcpd"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by excodic on 2012-06-11
Hi.

I am trying to make ipv6 work for my entire local network, and it seemed it was not as easy as i first seemed to believe. For this, i am using a tunnel from HE-net as my ISP don't offer native ipv6 at this point.

My network setup is following

eth0 - internet w/public ip
eth2 - local 192.168.2.0 network
sit0 - he-net tunnel
sit1 - he-net tunnel

i already have a working dhcpd server for the ipv4 network, with working local dns etc. Ubuntu 12.04 has a method of running 2 dhcpd's at one time, one for ipv4 and one for ipv6, as i understood that it is not possible to combine them at this point.

I added a ipv6 address from my routed subnet to eth2 as static, config looks like this (i had to modify the ip's before i could post)

iface eth2 inet6 static
 address 2001:470:00:00::00 (routed /64 ip)
 netmask 64
 gatway 2001:470:00:00::2 (client ipv6 ip)

ipv6 already working on the box as is, so no changes done there. i tried to connect to irc with the ipv6 i added to eth2, and it worked perfectly.


Next, i installed radvd and edited /etc/radvd.conf to look like this


interface eth2
{
  AdvSendAdvert on;
  AdvHomeAgentFlag off;
  MinRtrAdvInterval 30;
  MaxRtrAdvInterval 100;
  prefix 2001:470:00:00::/64
  {
    AdvOnLink on;
    AdvAutonomous on;
    AdvRouterAddr on;
  };
};

after this i created /etc/dhcp/dhcpd6.conf and made it look like this


ddns-update-style none;
default-lease-time 43200;
max-lease-time 43200;
authoritative;
log-facility local7;
subnet6 2001:470:00:00::/64 {
  range6 2001:470:00:00::110 2001:470:00:00::200;
  option dhcp6.name-servers 2001:470:20::2;
  option dhcp6.domain-search "he.net";
}

I then restarted radvd, dhcpd6 and the network interfaces. This is the part i don't understand greatly (i'm not a ipv6 expert); all my local computers somehow receive 2x ipv6 addresses that seems to be within my routed /64, but the .leases file show's nothing, neither can i ping any ipv6 ip out there.

After some more googling i found out i had to add/replace these lines in /etc/sysctl.conf

net.ipv4.ip_forward=1 
net.ipv6.conf.all.forwarding=1

now i did a sudo sysctl -p which shows me the output above. Nothing changes, i still cannot access ipv6 on my local machines, and i assume i have done something wrong, or maybe there is something i didn't do but should do. I am out of ideas, any pointers or help would be appreciated.

---

