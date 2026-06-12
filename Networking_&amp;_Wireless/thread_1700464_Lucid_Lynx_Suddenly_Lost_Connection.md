---
title: "Lucid Lynx Suddenly Lost Connection"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by FireDemonSiC on 2011-03-05
Seem to have a pretty complicated problem here that I have been trying to figure out for the past 4 hours.

All of a sudden without rhyme or reason, My Lucid Lynx install stopped connecting to my network.  This was without any intervention from me as I did not modify install or change anything prior to this happening.

What I have gathered so far is that upon initial boot eth0 seems to always be disabled.  So I ifconfig eth0 up to bring it back online.  All the settings in the network applet seem to be intact for my manual network that has DHCP disabled.  Let me re-iterate that these settings worked fine for months then all of a sudden something went belly up.  The same machine will connect fine with the same settings from within Win7.

ifconfig command shows both eth0 and the loopback interface but eth0 never manages to secure the 192.168.1.3 address that it should have.  ping 192.168.1.1 returns "Network unreachable" so it appears the connection is being cut off at the machine and not the router.

/etc/network/interfaces only shows two lines regarding the loopback interface and nothing else; eth0 seems non-existant within this file which I find odd.

Well guys, where to start?

---

