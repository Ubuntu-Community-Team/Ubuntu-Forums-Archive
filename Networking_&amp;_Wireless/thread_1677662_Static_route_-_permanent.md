---
title: "Static route - permanent"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by markh1289 on 2011-01-29
I searched and tried various things but can't get default route to be permanent through a reboot.


Why does this contents,
auto lo
iface lo inet loopback
up route add -net 0.0.0.0/0 gw 192.168.0.1 dev eth0

in file,
/etc/network/interfaces
-rwxr-xr-x 1 root root 84 2010-12-05 22:39 interfaces

then reboot, not give default route?
It only gives,
mark@mark-Ubuntu-10:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.128 U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
mark@mark-Ubuntu-10:~$ 

If I,
sudo route add -net 0.0.0.0/0 gw 192.168.0.1 dev eth0

then I get,
Mark@mark-Ubuntu-10:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.128 U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
mark@mark-Ubuntu-10:~$
- as desired

- but I want to get this immediately after a reboot.
Attempting to use the GUI to add default route has been entirely unsuccessful.

I also tried putting,
/sbin/route add -net default gw 192.168.0.1 dev eth0
into,
/etc/network//if-up.d/static-route

where static-route permission are thus,
-rwxr-xr-x 1 root root   53 2011-01-29 18:53 static-route

Your help would be appreciated.

Running:
Ubuntu 10.04 LTS
                - the Lucid Lynx - released in April 2010

---

