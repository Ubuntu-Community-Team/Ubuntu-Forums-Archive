---
title: "remote desktop"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by krishna1650 on 2008-12-12
hi everybody.
can remote desktop can connect a machine from anywhere through internet ?
if yes how to set up in ubuntu 8.10 ?


thanks.

---

### Post by HermanAB on 2008-12-12
To connect to Windows machines, enable remote desktop on port 3389/tcp, then use rdesktop to connect from Linux.

To connect to a Linux machine, install OpenSSH-Server on port 22/tcp, then connect from Windows using Xming and PuTTY.

Cheers,

Herman

---

### Post by krishna1650 on 2008-12-12
> **HermanAB said:**
> To connect to Windows machines, enable remote desktop on port 3389/tcp, then use rdesktop to connect from Linux.

To connect to a Linux machine, install OpenSSH-Server on port 22/tcp, then connect from Windows using Xming and PuTTY.

Cheers,

Herman

it will helpful if you tell the steps of installing & configuring openssh-server.

---

