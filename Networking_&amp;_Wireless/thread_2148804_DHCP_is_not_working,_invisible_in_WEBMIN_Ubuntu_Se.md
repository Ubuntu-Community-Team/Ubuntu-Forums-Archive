---
title: "DHCP is not working, invisible in WEBMIN Ubuntu Server 12.04 [SOLVED]"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by RikardSvenningsen on 2013-05-26
You can't configure DHCP from the WEBMIN.
It seems to be a name change from dhcpd3-server to isc-dhcp-server.
I have changed the WEBMIN (/etc/webmin/dhcp/dhcp.conf)
It now looks like this, and now it can be mananged by the WEBMIN:

lease_file=/var/lib/dhcp/dhcpd.leases
display_max=100
lease_tz=0
interfaces_type=debian
show_mac=0
stop_cmd=/etc/init.d/isc-dhcp-server stop
dhcpd_conf=/etc/dhcp/dhcpd.conf
pid_file=/var/run/isc-dhcp-server/dhcpd.pid
restart_cmd=/etc/init.d/isc-dhcp-server restart
desc_name=0
dhcpd_nocols=5
dhcpd_path=/usr/sbin/dhcpd
start_cmd=/etc/init.d/isc-dhcp-server start
group_name=0
lease_sort=0
show_ip=0
dhcpd_version=4.1
dhcpd_size=819364
dhcpd_mtime=1352328852

I don't know if there is any configuration difference between dhcpd3-server and isc-dhcp-server. to my knowledge it's the same.

---

