---
title: "kvpnc disconnects after 24 seconds"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by And-car on 2009-07-14
Anybody know why this might be? Consistently getting disconnect after 24 seconds. Have checked confiog and can't see any settings that would cause it. Thnx

---

### Post by johnnyis42 on 2009-07-18
Kvpnc uses the VPN gateway as the default address to check connection status.  It sounds liek you had the same problem I did where your VPN server (Cisco ASA?) blocks ping requests.

Fix this by either:

-Go in to KVPNC under the 'network' section, 'general' sub-section and disable the "use connection status check"

-or-

-In the same section, change the ip address to ping to some other ping-able internal address.

As I understand it, the 1 interval 4 success setting amounts to 24 seconds and then kvpnc reloads.

Cheers

---

### Post by And-car on 2009-07-19
Thank you that has fixed that issue. Onwards now the next problem - the server does not seem to be responding. Citrix Receiver window "Connecting..." just hangs , doesn't even time out. Any ideas gratefully received!

---

