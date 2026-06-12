---
title: "front end hangs on recordings menu"
date: 2008-09-22
forum: Mythbuntu
---

### Post by mark467 on 2008-09-22
my front end hangs sometimes on the menu of my recordings. remote and kb stop responding and the little thumbnail animation freezes. it can last from 15 sec to 2 min. any ideas on where to look for problems? I tried a clean reinstall same issue. machine is a p4 3ghz 1 gb ram nvidia 5900 card and std ide drive on wired 100mb network.

UPDATE I think I see a problem. In dmesg i am getting this alot

[64306.037092] txd read ptr: 0x154
[64306.037094] txs-behind:0x000105ea
[64306.037096] txs-before:0x00010036
[64306.084882] eth0: txs packet size do not coinsist with txd txd_:0x317d106c, txs_:0x00010036!
[64306.084889] txd read ptr: 0x15c
[64306.084892] txs-behind:0x000105ea
[64306.084894] txs-before:0x00010036
[64313.196756] NETDEV WATCHDOG: eth0: transmit timed out
[64314.733825] ATL2: eth0 NIC Link is Up<100 Mbps Full Duplex>

and watching my switch i see the link go down and back up

more ifo:
the link on the backend is whats going down. only happens when the front end is accessing it. i can ping it and its up for hours until front end starts to access it

---

### Post by mark467 on 2008-09-24
narrowed it down to when i go into media ; watch recordings. I can watch recordings (dvd iso's) fwd rwd and pause all smooth. It appears to be something coming from the front end causing the backend to down the eth0 and bring it back up. If someone can tell me what files or logs to post i would love to fix this.

Just found it that if i access mythweb on the backend it all works fine until i ask for the list of recorded programs. I can schedule , change settings etc, but when i click the recorded programs link it starts to populate the page then down she goes. (this is from a diff pc than front end also)

---

