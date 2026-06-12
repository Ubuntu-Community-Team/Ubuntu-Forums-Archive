---
title: "LDAP search on 9.04 stopped working"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by greenmoss on 2009-06-16
So, after upgrading a box to 9.04, LDAP queries stopped working. Here's an example of the breakage:

root@newhost:~# ldapsearch -x -d1
ldap_create
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP our.ldap.server:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 1.2.3.4:636
ldap_pvt_connect: fd: 3 tm: 2 async: 0
ldap_ndelay_on: 3
ldap_int_poll: fd: 3 tm: 2
ldap_is_sock_ready: 3
ldap_ndelay_off: 3
ldap_pvt_connect: 0
TLS: peer cert untrusted or revoked (0x102)
TLS: can't connect: (unknown error code).
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)


This works from other ldap-utils. I'm assuming it's not ldap-utils at the cause of the problem, but some underlying ldap library incompatibility. I looked online for information about this and was only able to find some notes that I don't understand: 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=478883](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=478883) 

My ldap-utils on the new host is package 2.4.11-0ubuntu6.1 on jaunty.

My slapd server is package 2.3.30-2ubuntu0.3 on feisty.

What's going on? How do I fix?

Thanks.

---

