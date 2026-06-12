---
title: "DHCP allow/deny to enable geo-block"
date: 2013-08-16
forum: Networking &amp; Wireless
---

### Post by graham2 on 2013-08-16
Hi 
I'm trying to bypass geo-blocking by configuring alternative DNS via DHCP. Some network devices (Roku) are unable to manually set DNS settings, so they must come from DHCP. I would set reservationss for a small number of known hosts and give them the bypass DNS via DHCP. But the known hosts only seem to get the main DNS settings. Any ideas where I'm going wrong? 
Thanks Graham


[FONT=courier new]ddns-update-style none;

default-lease-time 600;
max-lease-time 288000;

log-facility local7;

authoritative;

host host1 {
  hardware ethernet 00:1f:c5:fd:d8:91;
}
host host2 {
  hardware ethernet 00:1b:a9:18:95:39;
  fixed-address 192.168.0.11;
}
host host3 {
  hardware ethernet 00:1e:2a:85:01:b0;
  fixed-address 192.168.0.100;
}
host host4 {
  hardware ethernet 1c:7e:e5:10:59:ba;
  fixed-address 192.168.0.19;
}

[/FONT][FONT=courier new]subnet 192.168.0.0 netmask 255.255.255.0 {[/FONT][FONT=courier new]
  option routers 192.168.0.1;
  pool {
    range 192.168.0.10 192.168.0.188;
    option domain-name-servers 198.142.0.51, 211.29.132.12;
    allow unknown-clients;
    }
  pool {
    range 192.168.0.189 192.168.0.198;
    option domain-name-servers 69.197.169.9, 192.95.16.109;
    deny unknown-clients;
    }
}[/FONT]

---

### Post by graham2 on 2013-08-21
OK I sorted it out.
When the reserved hosts had the "fixed-address" statements, they didn't work. It's because the IP address was out of the range of the pool "deny unknown-clients". The dhcpd wanted to place it in the pool but the stated address was outside the pool, so it just gave it an "unknown" address.

When I removed the fixed-address statement, the reservation with the appropriate domain-name-server worked.

Hope this helps someone else struggling with this.

Graham

---

