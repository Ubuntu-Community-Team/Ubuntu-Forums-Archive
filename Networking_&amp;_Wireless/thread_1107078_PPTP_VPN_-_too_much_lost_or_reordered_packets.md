---
title: "PPTP VPN - too much lost or reordered packets"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by Eugene_ on 2009-03-26
Hello.
I have set up VPN on Ubuntu 8.10 with NetworkManager + network-manager-pptp without any problems. I can browse sites, download files...
But connection speed is about half of WinXP. Also when intensive browsing/downloading takes place my syslog gets flooded with messages like these at a rate about 20/sec:

> Mar 26 18:14:20 pptp[5774]: nm-pptp-service-5763 log[decaps_gre:pptp_gre.c:414]: buffering packet 8203 (expecting 8188, lost or reordered)
Mar 26 18:14:20 pptp[5774]: nm-pptp-service-5763 log[decaps_gre:pptp_gre.c:414]: buffering packet 8204 (expecting 8188, lost or reordered)
Mar 26 18:14:20 pptp[5774]: nm-pptp-service-5763 log[decaps_gre:pptp_gre.c:414]: buffering packet 8205 (expecting 8188, lost or reordered)

Can somebody point me to solution?

In "man pptp" I found:
--timeout <secs> Time to wait for reordered packets (0.01 to 10 secs)
But there is no such option in Network Manager GUI. Does anybody know how I can pass this option to pptp?

---

