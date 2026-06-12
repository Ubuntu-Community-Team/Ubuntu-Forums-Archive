---
title: "ISC DHCPv6 + DHCP + Apparmor = grrr..."
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by percula on 2011-08-26
Doing some work learning to setup some IPv6 services on 64-bit Natty. I have the default install of the ISC-DHCP-Server ver 4.1.1-P1

This server still doesn't support dual stack operations, so you have to run two instances, one for IPv4 and one for IPv6. So I created a new init.d script for DHCPv6 and tried to start it... Bang Apparmor denies it.

So I go and dig thru the Ubuntu help page for AppArmor [https://help.ubuntu.com/10.10/serverguide/C/apparmor.html](https://help.ubuntu.com/10.10/serverguide/C/apparmor.html)

Follow the directions there, I setup a new profile for v6, but I am still getting denied by AppArmor when I try to start the second instance of dhcpd for the IPv6 service.

Here is the syslog error message...


```
Aug 26 14:13:11 proxy kernel: [140544.944250] type=1400 audit(1314393191.365:2049): apparmor="DENIED" operation="mknod" parent=20703 profile="/usr/sbin/dhcpd" name="/var/lib/dhcp/dhcpd6.leases.1314393191" pid=20717 comm="dhcpd" requested_mask="c" denied_mask="c" fsuid=105 ouid=105

Aug 26 14:13:11 proxy kernel: [140544.947397] type=1400 audit(1314393191.365:2050): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/dhcpd" name="/var/run/dhcp-server/dhcpd6.pid" pid=20718 comm="dhcpd" requested_mask="c" denied_mask="c" fsuid=105 ouid=105
```

Here is the auto created AppArmor profile.

```
# Last Modified: Fri Aug 26 13:53:56 2011
#include <tunables/global>

/etc/init.d/isc-dhcp-server6 {
  #include <abstractions/base>



  /bin/dash ix,
  /etc/default/isc-dhcp-server r,
  /etc/init.d/isc-dhcp-server6 r,
  /etc/lsb-base-logging.sh r,
  /usr/sbin/dhcpd Ux,

}
```
Anyone have a working configuration for DHCPv4 and DHCPv6? Can you post your relevant files?

---

