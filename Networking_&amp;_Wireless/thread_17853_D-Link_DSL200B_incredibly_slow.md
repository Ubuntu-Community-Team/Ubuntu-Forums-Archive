---
title: "D-Link DSL200B incredibly slow"
date: 2005-03-03
forum: Networking &amp; Wireless
---

### Post by CAE on 2005-03-03
Hi guys. Just today, I've been trying to get my DSL200 rev B to work under Ubuntu (Warty). The software I'm using is [eciadsl](http://www.flashtux.org/index.php?lang=en) and [roaring penguin's](http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php) pppoe interface.

For the most part, I've been successful. The modem sync'd fine using the sync bin 04. I had a few more problems, but nothing a debug didn't give me enough information to fix. To my joy, I got connected about half an hour ago. I fired up Firefox and got... lag? Huh? I have a 1.5Mbit ADSL connection, yet I've browsed faster with a 28.8kbps modems. Pages just aren't loading. I've tried reconnecting, adjusting a few settings through adsl-setup however nothing's seemed to help.

Here's my output from adsl-status:
adsl-status: Link is up and running on interface ppp0
ppp0 Link encap:Point-to-Point Protocol
inet addr:220.244.243.17 P-t-P:202.7.162.166 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1492 Metric:1
RX packets:298 errors:0 dropped:0 overruns:0 frame:0
TX packets:329 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3
RX bytes:139944 (136.6 KiB) TX bytes:55540 (54.2 KiB)

I can also ping sites, and ping times look good:
# ping google.com -c 4
PING google.com (216.239.57.99) 56(84) bytes of data.
64 bytes from 216.239.57.99: icmp_seq=1 ttl=246 time=219 ms
64 bytes from 216.239.57.99: icmp_seq=2 ttl=246 time=218 ms
64 bytes from 216.239.57.99: icmp_seq=3 ttl=246 time=219 ms
64 bytes from 216.239.57.99: icmp_seq=4 ttl=246 time=220 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 218.799/219.628/220.216/0.541 ms

Anyone have any idea what might be wrong? I don't know what other information I can give you. If there's anything you want to ask, go ahead (perhaps explain how I should check it or whatever, seeing as I'm pretty new to this).

Thanks.

---

### Post by ember on 2005-03-03
Hmm ... that is strange ... have you tried adjusting the MTU?

---

### Post by CAE on 2005-03-03
[QUOTE=ember]Hmm ... that is strange ... have you tried adjusting the MTU?[/QUOTE]

How would I go about doing such?

---

### Post by ember on 2005-03-03
You can try lowering the MTU by:

ifconfig <device> mtu <value>

Try using a relativly low value and if that does help, raise it in reasonable steps. After rethinking it, I do not think this will really help, but at least you could give it a try.

---

