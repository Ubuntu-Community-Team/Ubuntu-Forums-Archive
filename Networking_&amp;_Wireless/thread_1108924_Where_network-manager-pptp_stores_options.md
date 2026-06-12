---
title: "Where network-manager-pptp stores options?"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by Eugene_ on 2009-03-28
I have setup VPN connection on my Ubuntu 8.10 via network-manager-pptp GUI. VPN is working but I'd like to change some options which network-manager passes to pppd and pptp-linux to improve performance.

ps aux gives me this command line:
> /usr/sbin/pppd pty /usr/sbin/pptp vpn.corbina.net --nolaunchpppd --logstring nm-pptp-service-5763 ipparam nm-pptp-service-5763 nodetach lock usepeerdns noipdefault nodefaultroute refuse-pap lcp-echo-failure 0 lcp-echo-interval 0 plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so

But I can't find where these options stored in my system so I can change them. Those mentioned in /etc/ppp/options* doesn't match with my command line.

Can somebody help?

---

