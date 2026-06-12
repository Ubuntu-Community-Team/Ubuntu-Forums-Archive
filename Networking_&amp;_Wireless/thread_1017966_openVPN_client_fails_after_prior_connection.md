---
title: "openVPN client fails after prior connection"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by hydrogen18 on 2008-12-21
I've got an openVPN server running on a debian 4.0rc3 box, it works fine. I can connect to it from anywhere with internet access, connect to my network, etc. I can use the client to connect just fine and it works, but if I disconnect and attempt to reconnect, the client attempts to use tun1, a non existent virtual device. It should be using tun0. Any idea why this is happening? If I restart and reconnect it works just fine.

---

