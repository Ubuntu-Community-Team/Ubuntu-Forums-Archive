---
title: "&quot;Connection reset by peer&quot; - network issue? how to debug?"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by sarraceno on 2010-02-05
Hi!

At my office I'm not able to do what ever I need when using eth0, but if I use wireless ap which is a bridge for the office lan I'm able to have fine communications.

As an example for this is that rdesktop drops with "Connection reset by peer", ssh sessions hangs, browser doesn't finish page fetch.
The strange is if I use windows, connections goes fine as I can see over office using eth0. Windows under VMWare if use bridge interface also goes fine, but VM interface NAT doesn't.

I'm using last VMWare Workstation over Ubuntu 9.10.

For this I believe I have some "noise" at office lan.
Wireshark shows some packet fragmentation issue, like the packets are arriving in non correct order.

Pls, do you know any way to find or quey what noise is doing such mess?
Or even what can be?

Can be some trojaned host over the network?
Network Servers are all Microsh.t!

Thanks all!

---

### Post by sarraceno on 2010-02-05
I been investigating other posts and also put some replies pointing to here.

So, it seems other folks like me are geting similar issue and not getting solved completly, except for the IP conflict.

Is there any TCP/UDP or even simply Ethernet sub protocol that handles with some network events that could lead to this?

Like some events intended to IDService that when activated or working could lead to this reaction?

Thanks all!

---

