---
title: "Hardening a Home firewall/proxy server"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by DariusVE on 2008-12-16
hi folks!,

I have a Ubuntu server 8.04 as Firewall / Proxy, also I installed sarg to see how my users interact and block some sites and protocols.

My network is:

- Ubuntu server with 2 NIC as Firewall / Proxy / Cache / DNS
- a switch for wired stations
- a wireless router for wifi clients with WAP and MAC filtering
- all the clients are Windows XP / Vista

I want to use OpenLDAP (slapd) to assign a User/Password for each user to access Internet, but I have some issues doing that.

What do you suggest? Any tool to administering it?

---

### Post by Cosimix on 2009-01-24
Hi mate.
I am studying OpenLDAP at the moment and am realising that is not that straight-forward also because you will probably need to change your PAM configuration as well. I have a similar scenario in my house and I will pass you on the solution as soon as I find it.  I hope you do as well.

Using LDAP would be a very smart authentication method, but however, you can use Squid to get the job done in the meantime. You also need to redirect port TCP ports 80,443 with iptables so that users are forced to authenticate and use Squid prior to access those services. Users will be able to use file sharing software (i.e. emule, transmission, limewire) though without authentication. See this HOWTO for Squid NCSA authentication and Squid Transparent Proxy Configuration: 

 
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid)

Cheers

---

