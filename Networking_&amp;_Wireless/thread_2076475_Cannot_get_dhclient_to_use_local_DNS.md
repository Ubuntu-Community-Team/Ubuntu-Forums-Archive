---
title: "Cannot get dhclient to use local DNS"
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by Lockheed on 2012-10-26
I have dnsmasq running on my localhost and it works fine with dhcpcd. I made it work by prepending nameserver to /etc/resolv.conf by creating the 
/etc/resolv.conf.head file: 
```
echo "nameserver 127.0.0.1" > /etc/resolv.conf.head
```

However, I want to use dhclient instead but I can't get it to work. The dnsmasq is just being ignored even if I add "prepend domain-name-servers 127.0.0.1;" to  /etc/dhclient.conf 

```
prepend domain-name-servers 127.0.0.1;
send host-name = pick-first-value(gethostname(), "ISC-dhclient");
send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
send dhcp-lease-time 3600;
supersede domain-search "fugue.com", "home.vix.com";
request subnet-mask, broadcast-address, time-offset, routers, domain-name, host-name;
#request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, host-name;
require subnet-mask, domain-name-servers;
timeout 60;
retry 60;
reboot 10;
select-timeout 5;
initial-interval 2;
script "/etc/dhclient-script";
media "-link0 -link1 -link2", "link0 link1";
reject 192.33.137.209;

alias {
  interface "ep0";
  fixed-address 192.5.5.213;
  option subnet-mask 255.255.255.255;
}

lease {
  interface "ep0";
  fixed-address 192.33.137.200;
  medium "link0 link1";
  option host-name "andare.swiftmedia.com";
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.33.137.255;
  option routers 192.33.137.250;
  option domain-name-servers 127.0.0.1;
  renew 2 2000/1/12 00:00:01;
  rebind 2 2000/1/12 00:00:01;
  expire 2 2000/1/12 00:00:01;
}
```

Can anyone see where's the issue?

---

