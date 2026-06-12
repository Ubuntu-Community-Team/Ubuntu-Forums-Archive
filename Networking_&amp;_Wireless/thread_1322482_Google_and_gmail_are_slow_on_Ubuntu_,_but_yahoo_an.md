---
title: "Google and gmail are slow on Ubuntu , but yahoo and bing are fast ! Strange"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by seshomaru samma on 2009-11-11
Hi, I have a strange problem.
We have a network of about 40 boxes behind a router. The router is set to use openDNS. Most machines are XP, we also have one Vista , one Mac and 3 Ubuntu's (Intrepid), one is a file server, one an ltsp server and one a thin client.
For some reason , on all Ubuntu boxes , google is very slow, anything related to google is slow, gmail, picasa, images etc...We are located in China but google.cn is just as slow, sometimes can take over one minute to load. On the same computers bing and yahoo load in a second or two. On all other non-Linux boxes , google loads in a split second and is very fast.
I have tried Firefox , Opera and Chrominum. I disabled ipv6 on the browser and the system itself. I looked at the hosts file (standard). 
Sometimes I get problems with other websites on Linux (like digg or slashdot) , when I check on the XP they load up instantly.
Does someone have an idea what to do or where to look?

---

### Post by dmizer on 2009-11-11
Try adding OpenDNS servers directly into the network settings on the Ubuntu boxes.

Right click on network-manager, select "edit connections", select your network adapter and click "edit". Then click the "IPv4 Settings" tab and change "Method" to "Automatic (DHCP) addresses only". Now you can add the OpenDNS servers in the "DNS servers" blank.

---

### Post by seshomaru samma on 2009-11-11
Thank you
I had to change resolv.conf as well
but it did the trick!

---

