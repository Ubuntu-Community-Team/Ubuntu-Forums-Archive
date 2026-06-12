---
title: "ldap client broke dns resolver"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by tomas_r on 2009-12-28
I played around with ldap server/client configurations. I set up an ldap server locally and started setting up a client locally. Not wanting to ruin my ability to log in, I removed the client stuff when I was done. 

I now have no DNS lookup capability and also using just IP addresses gives me problems. 

Note: This is only for the wired connection, the wireless still surprisingly works!

What was changed:

The following NEW packages will be installed:
  auth-client-config ldap-auth-client ldap-auth-config libnss-ldap libpam-ldap nscd

When I was done I removed nscd and libpam-ldap

Instantly, my dns resolver capabilities died. I can't even surf to IP addresses that I know. Ping works though. Package managers won't work because the network is smashed, even if I put IP's in /etc/hosts.

Things look normal in /etc/resolv.conf

I'm running ubuntu 8.10 i386. I dare not fiddle with nscd again with the wireless of fear of ruining also that connection.

Please advice what could be wrong.

---

