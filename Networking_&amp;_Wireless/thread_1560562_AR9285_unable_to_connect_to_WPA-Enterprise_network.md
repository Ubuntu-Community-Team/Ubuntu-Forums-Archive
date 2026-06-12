---
title: "AR9285 unable to connect to WPA-Enterprise networks"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by thePowersGang on 2010-08-25
I have a Toshiba NB300 netbook that has an Atheros AR9285 wireless chipset and is running Ubuntu 10.04 Lucid Lynx.
At my University there is a FreeRadius authenticated wireless network (called "UCC") that I would like to connect to.
Using NetworkManager I have created an automatic profile called "Auto UCC" that contains my user details for the connection.
When attempting to connect to the network, the NetworkManager icon spins for a couple of minutes and then presents me with the authentication dialog. If I re-enter my details (and disable the CA cert prompt), it repeats the process seemingly infinitely (spin-spin-spin, auth box)

Attached is a copy of the syslog from first attempting to connect to stopping the connection attempts.
The wireless card's 'lspci' line is
```

07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

---

### Post by tjaeger on 2010-08-25
I have the same problem. I'm getting an "unable to get IP address" error. None of the other solutions on the forum seem to work.

---

