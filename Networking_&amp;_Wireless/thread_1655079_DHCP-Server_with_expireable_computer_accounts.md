---
title: "DHCP-Server with expireable computer accounts"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by Torty77 on 2010-12-29
Hi,

at the moment we're running an isc dhcpd with about 300 clients to serve. Because of inconsequent maintaining i think we have about over 50 dead static client entries in our dhcpd.conf. So we want to change our construct.
Our aim is to allow a mac on the dhcp server to get an ip address. If this mac hasn't registered an ip address from the dhcp server for a time more than 90 days, the host entry gets disabled or deleted automatically. 
I'm searching for such kind of dhcp server configuration for many days. Have you any idea if there is a possibility to implement such a configuration?

Regards

Thorsten

---

### Post by kidders on 2010-12-30
Hi there,

The most straightforward option might be to use your DHCP server logs to identify MAC addresses that haven't leased an IP for a while. You could put together a short script to remove dead entries from dhcpd.conf, and have cron run it every few days.

The only problem that might crop up is that 90 days worth of DHCP logs for a network with 300 machines on it could be a bit of a monster. In practice, it might be better to cache lease timestamps in a database (eg sqlite), and use that to determine which static leases to remove.

Not very elegant, but should do the trick.

---

