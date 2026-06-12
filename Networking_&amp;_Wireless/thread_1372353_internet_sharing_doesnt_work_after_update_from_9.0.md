---
title: "internet sharing doesnt work after update from 9.04 to 9.10"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by lulaz on 2010-01-04
Hello,

Subject tells everything. After upgrading Jaunty to Karmic internet sharing (iptables) stoped working. Nothing in iptables configuration was changed. 
```

# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```Computers behind my ubuntu router can ping it, have access to it (apache, samba, etc.). Only internet isnt forwarding. Clients configuration is the same as before upgrade. 

Please help, thats very important and need to be fixed asap.

Regards, 
lulaz

---

### Post by puppywhacker on 2010-01-04
Show your "iptables -L -t nat" or use the lines below

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sysctl -w net.ipv4.conf.all.forwarding=1
iptables-save

```

---

### Post by lulaz on 2010-01-04
sysctl -w net.ipv4.conf.all.forwarding=1
That one helped, but its weird, as I have this set to "1" in sysctl.conf.
It seems that in Karmic something has been changed with sysctl and it doesnt load sysctl.conf.

Thanks !

---

