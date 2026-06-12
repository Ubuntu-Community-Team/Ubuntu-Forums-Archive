---
title: "OpenVPN Network Manager - private key problem"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by Swab on 2010-01-22
I'm running an up to date 10.04 so not expecting things to work, just wondering if this could be a bug.

Trying to setup an Open VPN connection in Network Manager using Password with Certificates (TLS) option.  Now my private key does not have a password however when I look in syslog to see why the connection fails I see the following.

```
Jan 22 22:27:14 qismat nm-openvpn[3937]: Cannot load private key file /home/user/openvpn/client.key: error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch

Jan 22 22:27:14 qismat nm-openvpn[3937]:Error: private key password verification failed
```

I've tried adding a password to the key but that makes no difference.

Any opinions?

---

### Post by Swab on 2010-01-25
bump

---

### Post by Swab on 2010-01-26
Turned out to be a case of PEBKAC :redface:

My certificate and key did not match, oops!

---

