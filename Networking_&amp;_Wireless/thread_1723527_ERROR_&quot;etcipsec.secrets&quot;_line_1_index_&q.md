---
title: "ERROR &quot;/etc/ipsec.secrets&quot; line 1: index &quot;:RSA&quot; illegal leading `:'"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by lament1_47 on 2011-04-07
Good day,

I am setting up a VPN server using Ubuntu 10.04 and openswan.  The target application is to serve VPN in IPSEC transport mode to roadwarriors with PCs or smartphones with X.509 authentication.

I created and  installed X.509 certificate and key with openssl.  The host private key name is "VPN-server-XXX.com.key" and its password is "my_secret".

The ipsec.secrets file is a single line:

:RSA VPN-server-XXX.com.key "my_secret"

also tried 

:RSA VPN-server-XXX.com.pem "my_secret"

The problem is that I cannot negociate a phase 1; the 'ipsec verify' returns OK to everything (except OE), including to "Checking for RSA private key (/etc/ipsec.secrets)", but the 'ipsec secrets' command (and the log) seems to mis-interpret the ipsec.secrets file and returns:

003 ERROR "/etc/ipsec.secrets" line 1: index ":RSA" illegal leading `:' in IPv6 numeric address
003  ERROR "/etc/ipsec.secrets" line 1: index  "/etc/ipsec.d/private/VPN-server-XXX.com.key" illegal (non-DNS-name)  character in name
003 ERROR "/etc/ipsec.secrets" line 1: index ""my_secret"" illegal (non-DNS-name) character in name
003 "/etc/ipsec.secrets" line 1: unexpected end of id list

I have read the openswan man pages, tried some syntax changes, without any improvment.

Would anybody have a suggestion?

Thanks in advance

---

