---
title: "dhcpv6 reply but interface address not assigned"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by helpmelearn on 2011-10-28
Hi,
I am trying to get ISC dhcpv6 server assign addresses to my lucid client (4.2.2 ISC dhclient).

I see the server's reply with tcpdump on the dhcp server. AND I see the client machine receive reply packet -- yet ip -6 addr show does not show the address configured.

Please see the attached image for the message seen on the client.

The configuration file on server:

/etc/dhcp/dhcp6.conf
authoritative;
update-static-leases off;
subnet6 fd1e:9b0f:2212:3028::/64 {
        range6 fd1e:9b0f:2212:3028:223:9cff:fe16:f702 fd1e:9b0f:2212:3028:223:9cff:fe16:f702;
        preferred-lifetime 360;
}

It shouldn't matter but I'll just mention that my dhcp client is a lucid VM.
ANY help would be great. Thanks!

---

### Post by poolet on 2011-10-29
strange!!! but do you have contact with your ISP support??  can they allow loopback for ipv6?? also some time help to restore your modem... Another thing, try to flash dns may helps you!!!!

---

