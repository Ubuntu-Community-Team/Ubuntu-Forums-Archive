---
title: "No internet connection"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by geomcewan on 2009-12-18
Can't get online using a new Linksys wrt 54g2 router - do I need to change the MAC address or IP settings?
Or is there a driver I need to download?
Thanks for any help, sorry about re posting but I'm at a total loss as to what to try next.

---

### Post by linux6994 on 2009-12-18
The WRTG54 router will get you on the Internet jsut a few things to do first:

1. The router has a WAN port for the connection to the DSL or Cable modem.
2. The LAN ports will connect to your PC via an ethernet cable to your eth0.
3. You need to know if your ISP is requiring PPPoe as in DSL or DHCP as is most cable providers use.
4. No additional drivers are required to talk to your Linksys.
5. When you plug in to it go to Network manager connection information and you should see 192.168.1.1 or 15.1 under the gateway info, configure the wireless as soon as possible since default could be open unencrypted access.

good luck

---

