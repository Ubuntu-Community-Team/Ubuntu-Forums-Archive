---
title: "Created bridge, now cannot use wireless"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by worx101 on 2008-12-03
Ok, I am using a bridge on my work notebook, as I use alot of vm's... but as soon as I set my bridge up... the wireless doesn't work...

Any advice? :(

cat of /etc/network/intefaces

auto lo eth0 tap1 br0

iface lo inet loopback

iface eth0 inet manual

iface tap1 inet manual
  tunctl_user mchenryb

iface br0 inet dhcp
  bridge_ports eth0 tap1
  pre-up ip link set eth0 promisc on

---

### Post by worx101 on 2008-12-04
bunt

---

### Post by worx101 on 2008-12-07
Help? :)

Ubuntu 8.10

---

### Post by worx101 on 2008-12-11
No help? :(

ok....  guess i didn't need wireless on my notebook anyway

:-({|=

---

