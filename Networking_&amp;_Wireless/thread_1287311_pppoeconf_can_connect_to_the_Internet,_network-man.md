---
title: "pppoeconf can connect to the Internet, network-manager applet can't"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by cloudscream on 2009-10-10
Since using Karmic, I wasn't able to establish a DSL connection using the Network Manager. In Jaunty, it was as simple as entering the username and password. In Karmic, Network Manager always fails to connect to the Internet.

I have to use pppoeconf everytime I go online. So that means Network Manager is pretty useless for me. Any ideas for NM to connect again to pppoe?

I am using Karmic amd64 beta with packages updated to the latest version.

---

### Post by Marat89 on 2009-10-10
BUMP
Same probs here :(

---

### Post by cloudscream on 2009-10-14
It's always like "Connecting...Connecting...Connecting... Disconnected." xD

---

### Post by n0_mad on 2009-10-21
same problem for me

---

### Post by Steven3k on 2009-10-26
Here it is a bug report on launchpad regarding this issue:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205)

---

### Post by cloudscream on 2009-10-29
^Thank you very much! :) I don't know 'what' to file in the bug report so it's good someone already did it on Launchpad.

---

### Post by shredder12 on 2009-10-29
does your network manager says "device unmanaged" for wired networks when your left click on its icon..

---

### Post by meho_r on 2009-10-29
Same here. It simply tries and then disconnects. No messages at all.

---

### Post by cloudscream on 2009-11-03
> **shredder12 said:**
> does your network manager says "device unmanaged" for wired networks when your left click on its icon..

No. I am aware that pppoeconf locks network management so I have to uncomment the entries it wrote in /etc/network/interfaces. It's just that I can setup the DSL setting in network manager but it just won't connect.

edit:
**IT IS NOW FIXED** (well, at least, for me). Thanks to Alexander Sack. :) Just update using his ppa. [https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)

---

