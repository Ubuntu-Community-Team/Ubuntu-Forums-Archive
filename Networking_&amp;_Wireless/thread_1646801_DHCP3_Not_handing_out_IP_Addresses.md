---
title: "DHCP3 Not handing out IP Addresses"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by J0hnnyBr@v0 on 2010-12-16
All,

I have a script I have been using for a while, but seems to have broken in the latest upgrade.

The script takes some user input, builds a dhcp config file and then starts dhcp server on the specified interface.

I can verify that everything works, as far as computers connecting, the config file populates properly, etc.  Only thing is no IPs are given to connecting clients.  Below are the snippets of code, if the full script function is required, I'd be happy to provide it as well.

```
echo "Creating a dhcpd.conf to assign addresses to clients that connect to us"
echo "default-lease-time 600;" > /$fldrpath/$fldrtime/dhcpd.conf
echo "max-lease-time 720;"  >> /$fldrpath/$fldrtime/dhcpd.conf
echo "ddns-update-style none;" >> /$fldrpath/$fldrtime/dhcpd.conf
echo "authoritative;"  >> /$fldrpath/$fldrtime/dhcpd.conf
echo "log-facility local7;"  >> /$fldrpath/$fldrtime/dhcpd.conf
echo "subnet "$ATSUB" netmask "$ATSNM" {"  >> /$fldrpath/$fldrtime/dhcpd.conf
echo "range "$ATRANGE";"  >> /$fldrpath/$fldrtime/dhcpd.conf
echo "option routers $ATIP;"  >> /$fldrpath/$fldrtime/dhcpd.conf
echo "option domain-name-servers $ATDNS;"  >> /$fldrpath/$fldrtime/dhcpd.conf
echo "}"  >> /$fldrpath/$fldrtime/dhcpd.conf
#
echo 'DHCP server starting on our airdrop-ng interface (at0)'
dhcpd3 -f -cf /$fldrpath/$fldrtime/dhcpd.conf -pf /var/run/dhcp3-server/dhcp.pid at0 &

```

Also, I am not getting any errors in the syslog.

Best Regards,
Eric

---

