---
title: "Wireless auto reconnect and quagga problem"
date: 2011-11-27
forum: Networking &amp; Wireless
---

### Post by --Ja-- on 2011-11-27
Hi all!

I have Ubuntu 11.04 posing as wireless node. Everything is working more or less ok, but I'm having two problems that are driving me crazy.

1. How to make Ubuntu auto reconnect to the neighbouring wireless node when it loses connection. Neighbouring node is a gateway to the Internet, and it gets rebooted twice a day. I need Ubuntu 11.04 to automatically reconnect to it's neighbour when it becomes available again.

2. I'm running Quagga (ospfd + zebra) on the network. Network consists of routers with different versions of linux (WifiWare 1.4.1, Ubuntu server 8.10...all outdated, I know). But the thing is, everything was working fine until I introduced Ubuntu 11.04 to the network. Suddenly nodes that are neighbours of Ubuntu 11.04 are losing routes that are coming from Ubuntu 11.04. If I restart quagga service on the neighbouring node, most times everything goes back to normal.

Is there a cure for any of these problems? At the moment I'm running some bash scripts in the background which detect and fix those problem, but I'd rather solve these issues then work around them...

Thank you!

---

### Post by --Ja-- on 2011-11-30
Anyone?

---

