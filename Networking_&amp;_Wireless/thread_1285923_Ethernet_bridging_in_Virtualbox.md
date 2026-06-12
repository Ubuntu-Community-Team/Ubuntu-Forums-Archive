---
title: "Ethernet bridging in Virtualbox"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by box2 on 2009-10-08
I am running into a problem running virtualbox-ose 2.1.4 (Running Jaunty 9.04 64bit).  I have 3 virtual machines set up fine.  I have set up on the host box ethernet tunneling as such:

/etc/network/interfaces:
```

# For Virtualized Interfaces
iface eth0 inet manual

auto tap0 tap1 tap2 tap3 tap4 tap5
iface tap0 inet manual
tunctl_user <username>
iface tap1 inet manual
tunctl_user <username>
iface tap2 inet manual
tunctl_user <username>
iface tap3 inet manual
tunctl_user <username>
iface tap4 inet manual
tunctl_user <username>
iface tap5 inet manual
tunctl_user <username>

auto br0
iface br0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
bridge_maxwait 0
bridge_ports eth0 tap0 tap1 tap2 tap3 tap4 tap5
bridge_fd 0

```

(Of course, <username> is replaced with the actual non-root user that I set these up for and which all the VM's run under).

So the deal is, I have set the first 3 virtual machines to use tun0, tun1, and tun2, (using Host Interface feature in Virtualbox) they bring up eth devices just fine and in their own tiny little /etc/network/inferfaces file I set them to static IPs and they work fine with the network and can even serve applications to the network.

My problem is that my 4th virtual machine (which i have remade over and over and is set up in exactly the same way, using either tun3 or 4 or 5) does not recognize the external network.  I can ping all the other virtual machines and host OS, but it cannot reach the internet or any other machines outside of the host machine.  I am wondering if this is a Virtualbox issue or if it is in some way a limitation of ethernet bridging on Ubuntu.  I really have no idea, nor how to debug this issue.

Does anyone have some input for this situation?

---

### Post by box2 on 2009-10-08
As it seems, the Virtualbox team at Sun says that there is no limit on the OSE version for how many devices can use TAP interfaces, so the limit must be on the Ubuntu side.  Anyone know how I can increase this limit?

---

### Post by box2 on 2009-10-08
I ended up fixing this issue by moving my configuration from /etc/network/interfaces to /etc/rc.local

Here is the new config for reference to other people:
```

#Enable Virtualbox Host Interface Networking
/sbin/modprobe tun
/usr/sbin/tunctl -u <username> -t tap0
/sbin/ifconfig tap0 0.0.0.0 promisc up
/usr/sbin/tunctl -u <username> -t tap1
/sbin/ifconfig tap1 0.0.0.0 promisc up
/usr/sbin/tunctl -u <username> -t tap2
/sbin/ifconfig tap2 0.0.0.0 promisc up
/usr/sbin/tunctl -u <username> -t tap3
/sbin/ifconfig tap3 0.0.0.0 promisc up
/usr/sbin/tunctl -u <username> -t tap4
/sbin/ifconfig tap4 0.0.0.0 promisc up
/bin/chmod 0666 /dev/net/tun
/usr/sbin/brctl addbr br0
/usr/sbin/brctl addif br0 eth0
/usr/sbin/brctl addif br0 tap0
/usr/sbin/brctl addif br0 tap1
/usr/sbin/brctl addif br0 tap2
/usr/sbin/brctl addif br0 tap3
/usr/sbin/brctl addif br0 tap4
/sbin/ifconfig br0 192.168.0.100 netmask 255.255.255.0 broadcast 192.168.0.255 up
/sbin/ifconfig eth0 0.0.0.0 promisc up
/sbin/route add default gw 192.168.0.1 

exit 0

```

Weee!  Good luck to everyone else out there with Virtualbox, it rocks!

---

