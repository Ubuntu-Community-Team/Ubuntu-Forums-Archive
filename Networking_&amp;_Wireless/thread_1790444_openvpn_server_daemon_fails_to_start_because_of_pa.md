---
title: "openvpn server daemon fails to start because of password issue"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by MartinusEx on 2011-06-25
Hi out there,

happily working with the installation of openvpn.
From the terminal all works well but I'm asked to enter the passphrase

Openvpn should start as a daemon by now but doesn't.
server.conf is provided in /etc/openvpn

This is the reason from /var/log/daemon.log

```
Jun 25 07:16:56 kaa ovpn-server[926]: Cannot load private key file /etc/ssl/private/server-key.pem: error:0906A068:PEM routines:PEM_do_header:bad password read: error:140B0009:SSL routines:SSL_CTX_use_PrivateKey_file:PEM lib
Jun 25 07:16:56 kaa ovpn-server[926]: Error: private key password verification failed
Jun 25 07:16:56 kaa ovpn-server[926]: Exiting
```

There are two possibilities to solve this:

1. Build a new server key without issuing a passphrase
2. Tell openvpn the current passphrase to open the key file

I'd like to go for #2 BUT I do NOT kow where I can tell openvpn the passphrase

Can anybody provide support??

THX

Martin

---

