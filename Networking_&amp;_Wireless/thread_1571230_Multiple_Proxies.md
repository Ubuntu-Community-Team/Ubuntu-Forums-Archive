---
title: "Multiple Proxies"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by tbrammer on 2010-09-09
All,

While the title may sound ridiculous, here's what I'm dealing with.

I  have a 10.04 box that I'm responsible for on a network that I have  absolutely no control over. This network uses a proxy that requires  manual configuration of each station, so these settings must be manually  put in. By default the box is running a local squid proxy as a simple  webfilter through Firefox.

The problems presented by this are  numerous, as we all know that setting the proxy in Gnome does not truly  set a system wide proxy. Along with this, setting the Gnome proxy  doesn't help Firefox access the internet, as squid is still attempting  to access it directly, which Firefox is configured to use.

All  that being said, is there a way through iptables to direct all traffic  to the networks proxy while still maintaining the use of squid in  Firefox? I know there are numerous guides on using squid transparently,  so could I make use of the same technique to use the schools proxy  transparently? Normally it is only done by modifying a port, but I would  need to specify an entire address along with the port

This whole thing is a huge cluster f#$k, and I appreciate any help in advance.

-Tim

---

