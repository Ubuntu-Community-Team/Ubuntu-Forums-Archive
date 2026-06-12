---
title: "Problem with DHCP in Ubuntu Server 9.04 on a network?"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by Pascal11110 on 2009-10-21
I am setting up a Ubuntu server at my school. The school has local DHCP. I installed Ubuntu server onto the computer, and installed the gnome desktop on it. After that I could access the internet, and all of the network shares, but for some reason the server took the ip adress 192.168.0.15 when it was already in use by  a printer on the network. I ended up having to reinstall the server because of some "unrelated technical difficulties" and this second time it took the same IP. I could set it up statically with no problem, but I'd rather get the DHCP to work. Why is this server taking a reserved IP, when DHCP works fine for all of the other computers on the network? Thanks for any help in advance.

---

### Post by Iowan on 2009-10-22
Post */etc/network/interfaces*.

---

