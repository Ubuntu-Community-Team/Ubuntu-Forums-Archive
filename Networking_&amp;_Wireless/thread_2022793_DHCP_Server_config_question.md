---
title: "DHCP Server config question"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by adepaolis on 2012-07-11
Hey All,

I am playing with ubuntu and trying to setup the dhcp server.  I am trying to set it up so that there is a total of 1000 ip addresses.  What is happening is only the ip addresses in the 192.168.0 is being used and the dhcp server is not handing out ip addresses in the 192.168.1.0, 192.168.2.0, or 192.168.3.0 subnet.

 This is my configuration:

# option definitions common to all supported networks...
option domain-name-servers 208.67.222.222, 208.67.220.220;
option subnet-mask 255.255.252.0;
option broadcast-address 192.168.3.255;
option routers 192.168.0.1;
default-lease-time 3600;
max-lease-time 43200;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.125 192.168.0.254;
}

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.254;
}

subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.2 192.168.2.254;
}

subnet 192.168.3.0 netmask 255.255.255.0 {
  range 192.168.3.2 192.168.3.254;
}

---

### Post by adepaolis on 2012-07-11
I think I solved my problem with some searching inthe forum.  Basically I needed to add the shared-network command to group the subnets like such:

# option definitions common to all supported networks...
option domain-name-servers 208.67.222.222, 208.67.220.220;
option subnet-mask 255.255.252.0;
option broadcast-address 192.168.3.255;
option routers 192.168.0.1;
default-lease-time 3600;
max-lease-time 43200;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

shared-network guest{
subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.125 192.168.0.254;
}

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.2 192.168.1.254;
}

subnet 192.168.2.0 netmask 255.255.255.0 {
range 192.168.2.2 192.168.2.254;
}

subnet 192.168.3.0 netmask 255.255.255.0 {
range 192.168.3.2 192.168.3.254;
}
}

---

### Post by SeijiSensei on 2012-07-11
That's one solution, but why not just use a different netmask than /24?  A /22 gives you 1,022 usable addresses.  That translates to a netmask of 255.255.252.0, or 11111111111111111111110000000000.

For a relatively clear explanation of "classless" routing, read [this wiki page]("http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing"); for more technical details, read [RFC 4632]("http://tools.ietf.org/html/rfc4632").

---

