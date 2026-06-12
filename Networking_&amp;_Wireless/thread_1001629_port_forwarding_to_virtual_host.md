---
title: "port forwarding to virtual host"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by olahlacko on 2008-12-04
Dear Colleagues,

I have created a VMware based XP virtual host on Ubuntu 8.10. I would like to dedicate a port for an application, what is running on the virtual XP.
The network topology is the following:

Router:
external connection - public IP from ISP
internal connection - 192.168.1.1
port forward - enabled

Ubuntu:
external connection, eth0 - 192.168.1.100
internal connection, vmnet8 - 192.168.79.2

XP IP (virtual) - 192.168.79.10

I have inserted the following entries into the iptables script below, unfortunately with no success. The port is closed from the application.
# PORT FORWARD
iptables -A INPUT -p tcp --dport 19897 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 19897 -j ACCEPT
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 19897 -j DNAT --to-destination 192.168.79.10:19897
iptables -t nat -A POSTROUTING -o vmnet8 -p tcp --dport 19897 -j SNAT --to-source 192.168.79.2

As I know in the POSTROUTING rule I have to define the source as a gateway. In my read in this case the gateway is the vmnet8, but I am not sure. Please correct me if I wrong.

Thank you all,
Laci

---

### Post by olahlacko on 2008-12-04
here is the answer, maybe one of you can use it....
edit the "/etc/vmware/vmnet8/nat/nat.conf" file

insert this entry into the [incomingtcp] section:
19897 = 192.168.79.10:19897

thank you,
Laci

---

