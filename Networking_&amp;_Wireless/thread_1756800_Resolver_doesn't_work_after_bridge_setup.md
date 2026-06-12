---
title: "Resolver doesn't work after bridge setup"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by dolsonj on 2011-05-12
I have install Ubuntu 10.04 on a server. Networking and resolver were working fine. In preparation for setting up 3 virtual servers, I set up bridging in /etc/network/interfaces and restarted networking. Before setting up the bridging, the resolver worked fine. After setting up the bridging, the resolver no longer works on the host server. (The resolver and networking on the virtual servers work fine).
 
Here is my initial interfaces file contents:
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 1XX.2XX.1XX.128
netmask 255.255.255.0
network 1XX.2XX.1XX.0
broadcast 1XX.2XX.1XX.255
gateway 1XX.2XX.1XX.1
 
Here is what was added for bridging for 3 virtual servers:
# Second interface - bridged for virt machine 1
auto eth1
iface eth1 inet manual
auto br1
iface br1 inet static
address 1XX.2XX.1XX.160
netmask 255.255.255.0
network 1XX.2XX.1XX.0
broadcast 1XX.2XX.1XX.255
gateway 1XX.2XX.1XX.1
bridge_ports eth1
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
# Third interface - bridged for virt machine 2
auto eth2
iface eth2 inet manual
auto br2
iface br2 inet static
address 1XX.2XX.1XX.161
netmask 255.255.255.0
network 1XX.2XX.1XX.0
broadcast 1XX.2XX.1XX.255
gateway 1XX.2XX.1XX.1
bridge_ports eth2
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
# Fourth interface - bridged for virt machine 3
auto eth3
iface eth3 inet manual
auto br3
iface br3 inet static
address 1XX.2XX.1XX.162
netmask 255.255.255.0
network 1XX.2XX.1XX.0
broadcast 1XX.2XX.1XX.255
gateway 1XX.2XX.1XX.1
bridge_ports eth3
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
 
(Note - some network information X'd out to disguise company information. resolvconf package not installed and /etc/resolv.conf unchanged after bridging).
 
Does anyone know why the resolver no longer works on the host server?

---

### Post by dolsonj on 2011-05-18
Found the answer to the problem myself at this link:
 
[http://serverfault.com/questions/101477/issue-with-multiple-bridging-for-kvm-hosts](http://serverfault.com/questions/101477/issue-with-multiple-bridging-for-kvm-hosts)
 
For all the bridge interfaces, changed the subnet mask to "255.255.255.255". Now resolver works on the host server.

---

### Post by matthew.mattoon on 2011-05-24
> **dolsonj said:**
> Found the answer to the problem myself at this link:
 
[http://serverfault.com/questions/101477/issue-with-multiple-bridging-for-kvm-hosts](http://serverfault.com/questions/101477/issue-with-multiple-bridging-for-kvm-hosts)
 
For all the bridge interfaces, changed the subnet mask to "255.255.255.255". Now resolver works on the host server.

This was most likely caused by having multiple interfaces with default gateways...  Changing the subnet mask invalidated the gateways on the bridge interfaces and everything works.  If you use the proper subnet mask on the bridge interfaces and then remove the gateway (ensuring that your primary interface or bridge has the correct gateway) then you should have the same result (with a little more understandable configuration.

-matt

---

