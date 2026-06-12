---
title: "network bridge help"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by mawe3661 on 2010-11-29
Hi!

I have one computer connected to the internet (eth0) and a bridge (bridge0) as well as a bluetooth device (pan1). I am trying to bridge pan1 and eth0 via bridge0, but there is probably somethin wrong in my /etc/network/interfaces: 

root@stereo:/etc/network# cat interfaces
auto eth0
iface eth0 inet manual

auto bridge0
iface bridge0 inet dhcp
  pre-up ifconfig eth0 down
  pre-up brctl addbr bridge0
  pre-up brctl addif bridge0 eth0
  pre-up ifconfig eth0 up
  post-down ifconfig eth0 down
  post-down brctl delif bridge0 eth0

auto pan1
iface pan1 inet manual
  pre-up brctl addbr bridge0
  pre-up brctl addif bridge0 $IFACE
  up ifconfig $IFACE 0.0.0.0 up
  down ifconfig $IFACE down
  post-down brctl delif bridge0 $IFACE

# The loopback network interface
auto lo
iface lo inet loopback
root@stereo:/etc/network# 


Any help would be much appreciated!

---

