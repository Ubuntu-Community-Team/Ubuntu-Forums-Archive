---
title: "eth1 + DHCP -&gt; Internet, eth0 -&gt; Linksys WRT54G + Provider DHCP"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by ot4uzdensky on 2010-06-25
):P Hello. 
I have a  small problem.
I have a Ubuntu 10.04  (I'm new to Linux) with two network cards eth0 and eth1. eth1 with DHCP ->  Internet, eth0 -> Linksys WRT54G, it 5 laptops with XP! Internet is available  only in ubuntu, when you connect to eth0 laptop with windows xp I see  the message - the network cable is not connected.  I really wanted to  connect from laptop or router to the network card eth0 he received Provider auto  DHCP setting  and went on the internet.  :popcorn:

Here is my headache. I very much counting on  your expertise and look forward to participate
Help Me Please![I] [-o<
[/I]

---

### Post by aeiah on 2010-06-25
is there a reason you can't just do: all computers -> WRT54G -> internet?

anyway, i think what you need is IP forwarding on your machine with eth0 and eth1, and masquerading set up in IPTables. this way, all laptop packets go from WRT54G's WAN -> eth0 -> eth1 -> internet

---

### Post by Iowan on 2010-06-25
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for ICS. I thought there was  section in the [server guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html"), but can't find it at the moment.

---

