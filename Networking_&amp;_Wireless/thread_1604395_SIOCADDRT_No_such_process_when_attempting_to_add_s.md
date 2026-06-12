---
title: "SIOCADDRT: No such process when attempting to add static route"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by mb850t@gmail.com on 2010-10-24
hi all - ubuntu LTS 10.0.4.  attempting following command:

'sudo route add -net 192.168.0.0 netmask 255.255.255.0 gw 69.XX.XX.XX' and getting following error:

SIOCADDRT: No such process

everything looks correct in my /etc/network/interfaces file.  what's going on?  i have an identical ubuntu server box and this command works fine on it.

thx-
m

---

### Post by SeijiSensei on 2010-10-24
Can you ping the 69.x.x.x gateway from this box?  Maybe you don't have a route established to the gateway?

---

### Post by elnoob on 2011-02-11
bumpa loompa... :confused:

---

