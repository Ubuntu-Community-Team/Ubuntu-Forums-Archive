---
title: "Bridge 2 vlan together"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by kerimbasol on 2010-10-16
# Bridge between eth0.2 and eth0.4
# written by Kerim BASOL
# E-Mail : [email]kerim@bayner.com[/email]
# Web : [http://www.bayner.com](http://www.bayner.com)
auto br0
#iface br0 inet dhcp
# For static configuration delete or comment out the above line and uncomment the following:
iface br0 inet static
  address 192.168.1.1
  netmask 255.255.255.0
  network 192.168.1.0
  pre-up ifconfig eth0 up
  pre-up vconfig add eth0 2
  pre-up vconfig add eth0 4
  pre-up brctl addbr br0
  pre-up brctl addif br0 eth0.2
  pre-up brctl addif br0 eth0.4
  pre-up ifconfig eth0.2 0.0.0.0
  pre-up ifconfig eth0.4 0.0.0.0
#This is old ubuntu and debian systems.
#Please ucomment line below
  post-up /etc/init.d/dhcp3-server restart
  post-down ifconfig eth0.2 down
  post-down ifconfig eth0.4 down
  post-down ifconfig br0 down
  post-down brctl delif br0 eth0.2
  post-down brctl delif br0 eth0.4
  post-down vconfig rem eth0.2
  post-down vconfig rem eth0.4
  post-down brctl delbr br0
#This is old ubuntu and debian systems.
#Please ucomment line below
  post-down /etc/init.d/dhcp3-server restart


-------------------------------------------------------
Add following scripts to /etc/sysctl.conf

net.ipv4.conf.all.proxy_arp = 1
------------------------------------------------------

if you encourage an error.Remove last script of /etc/sysctl.conf

---

### Post by kerimbasol on 2010-10-16
I forget to write first script place.The place of the first script is /etc/network/interfaces.Add there.:)

---

### Post by kerimbasol on 2010-10-16
May be use this.If you encourage an error.Instead of above script

-------------------------------------------------------
Add following scripts to /etc/sysctl.conf

net.ipv4.conf.br0.proxy_arp = 1
------------------------------------------------------

---

