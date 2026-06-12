---
title: "Tried to set static ip, but it keeps using dhcp in 8.04 server"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by thesoffish on 2009-04-24
I have tried following all the instructions I could find to use a static ip: editing /etc/network/interfaces, /etc/resolv.conf, etc, but when I do sudo /etc/init.d/networking restart it continues to give me a dynamic address with dhcp. I have tried editing /etc/dhcp3/dhclient.conf to use the static ip as an alias, and that works--i.e. it sets it as an alias for eth0:0, so that I can access the server through it, but it still continues to assign a dynamic ip as well to eth0, which is not what I want. If I uninstall dhcp3-client and restart networking it still gives me the static as an alias on eth0:0, but eth0 itself then has no ip and I can't access the internet.

The strange thing is I was able to use the static properly a week ago, but since then I have reinstalled the server. However I don't think I have done anything different this time, and I know the static ip itself is good since I can use it on other computers.

I feel like there is probably something stupid or obvious I am overlooking, so is there anything else I should be aware of or things I could try in resolving this problem?

---

### Post by AKviking on 2009-04-24
Could you post your /etc/network/interfaces here?

---

### Post by thesoffish on 2009-04-24
Haha... apparently the problem was that my interfaces file was just in /etc, rather than in /etc/network.

Sorry :) I will have to be sure to check that in the future..

---

