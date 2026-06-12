---
title: "Wireless Not Connecting"
date: 2012-09-25
forum: Networking &amp; Wireless
---

### Post by ctownstud00 on 2012-09-25
My wireless card can see networks, and when I try to connect to one, it starts the spinning icon, like it's trying, but then, after a few spins, it stops trying, giving no messages or errors.

Are there any logs I can check? I'm not sure how to diagnose and fix this issue.

I'm using Ubuntu 10.04 Netbook, with a USB plugin RT5370 wireless card. The netbook also has a built-in wireless card, but I use that for a software hotspot, so I don't use that to connect to the Internet, just to rebroadcast it.

Thanks for any help,
Sean

---

### Post by ctownstud00 on 2012-09-30
Can anyone guide me a little on this? I'm not sure where any logs are or how to check them.

---

### Post by ctownstud00 on 2012-10-02
After fiddling around, I found some logs (System->Administration->Log File Viewer) and I noticed this issue:

NetworkManager: <WARN>  nm_dhcp_client_start(): /sbin/dhclient does not exist.

I re-installed the DHCP3-Client package and everything is connecting again.

---

