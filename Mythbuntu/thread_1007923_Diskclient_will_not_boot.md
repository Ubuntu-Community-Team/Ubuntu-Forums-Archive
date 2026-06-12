---
title: "Diskclient will not boot"
date: 2008-12-10
forum: Mythbuntu
---

### Post by map7 on 2008-12-10
I have an eeepc with I'm trying to get working with my Mythbuntu server.  I've setup my server for diskless clients to connect and have tested this with another computer which works.

The problem I have on the eeepc is that the network interface is not the same device name as the server, ie: ath0 instead of eth0.  

When I try and boot using the network card on the eeepc 701 I get the error:
ipconfig: eth0 SIOCGIFINDEX: No such device
ipconfig: no devices to configure
/init: .: line 1: can't open /tmp/net-eth0.conf
[ 6.121127] Kernel panic - not syncing: Attempted to kill init!

Is there a way to add allow the ath0 network device for this one client?

---

### Post by map7 on 2008-12-16
Found that the problem maybe the special ethernet chipset that the eeepc uses:

[http://forum.eeeuser.com/viewtopic.php?pid=153913](http://forum.eeeuser.com/viewtopic.php?pid=153913)

---

