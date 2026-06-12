---
title: "Ethernet bridge kills internet connection"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by spongypants23 on 2009-11-19
I've built a bridge, br0, using the following script:

```

#!/bin/bash

#################################
# Set up Ethernet bridge on Linux
# Requires: bridge-utils
#################################

# Define Bridge Interface
br="br0"

# Define list of TAP interfaces to be bridged,
# for example tap="tap0 tap1 tap2".
tap="tap0"

# Define physical ethernet interface to be bridged
# with TAP interface(s) above.
eth="eth0"
eth_ip="192.168.1.201"
eth_netmask="255.255.255.0"
eth_broadcast="192.168.1.255"

for t in $tap; do
    openvpn --mktun --dev $t
done

brctl addbr $br
brctl addif $br $eth

for t in $tap; do
    brctl addif $br $t
done

for t in $tap; do
    ifconfig $t 0.0.0.0 promisc up
done

ifconfig $eth 0.0.0.0 promisc up

ifconfig $br $eth_ip netmask $eth_netmask broadcast $eth_broadcast

```
(Script provided by OpenVPN and modified to fit my network.)
And yes, bridge-utils is installed.


Problem is, once the bridge is started using this script (that is to say, brought up) it no longer has an internet connection.

I.e. it can ping 192.168.1.1 but not [www.google.se](www.google.se) (Swedish Google) with the message "Network is unreachable". I'm also getting reports from friends that they can't access the server via HTTP. Strange thing is, though, that I can.

If I reboot the server and don't bring the bridge up with the script everything works fine.

Any help?

---

### Post by Yoann Juet on 2009-11-19
Default gateway misdefined ? Otherwise, what is the output of the "ip addr" and "ip route" commands before and after the script execution ?

---

### Post by spongypants23 on 2009-11-19
> **Yoann Juet said:**
> Default gateway misdefined ? 
I'm not sure where that would be defined. The script isn't asking for it anywhere.

> **Yoann Juet said:**
> Otherwise, what is the output of the "ip addr" and "ip route" commands before and after the script execution ?

**Before:**
ip addr
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:0e:7f:64:fe:94 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.201/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::20e:7fff:fe64:fe94/64 scope link 
       valid_lft forever preferred_lft forever
3: tap0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 100
    link/ether 2e:aa:82:5d:7e:67 brd ff:ff:ff:ff:ff:ff
```

ip route
```
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.201 
default via 192.168.1.1 dev eth0  metric 100 
```

**After:**
ip addr
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,PROMISC,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:0e:7f:64:fe:94 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::20e:7fff:fe64:fe94/64 scope link 
       valid_lft forever preferred_lft forever
3: tap0: <BROADCAST,MULTICAST,PROMISC,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 100
    link/ether 2e:aa:82:5d:7e:67 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::2caa:82ff:fe5d:7e67/64 scope link 
       valid_lft forever preferred_lft forever
4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN 
    link/ether 00:0e:7f:64:fe:94 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.201/24 brd 192.168.1.255 scope global br0
    inet6 fe80::20e:7fff:fe64:fe94/64 scope link 
       valid_lft forever preferred_lft forever
```

ip route
```
192.168.1.0/24 dev br0  proto kernel  scope link  src 192.168.1.201 
```

---------

Additionally, I noticed this output while running the script, it may or may not have to do with anything:
```

Thu Nov 19 21:22:18 2009 Note: Cannot ioctl TUNSETIFF tap0: Device or resource busy (errno=16)
Thu Nov 19 21:22:18 2009 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Thu Nov 19 21:22:18 2009 Cannot open TUN/TAP dev /dev/tap0: No such file or directory (errno=2)

```

---

### Post by Yoann Juet on 2009-11-20
> **spongypants23 said:**
> 
ip route
```
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.201 
default via 192.168.1.1 dev eth0  metric 100 
```


Just try to execute the following commands :

ifconfig br0 up
ifconfig tap0 up
route add default gw 192.168.1.1


> Thu Nov 19 21:22:18 2009 Cannot open TUN/TAP dev /dev/tap0: No such file or directory (errno=2)

Not sure this is really important. tap0 interface has yet been created added.

---

### Post by spongypants23 on 2009-11-20
> **Yoann Juet said:**
> Just try to execute the following commands :

ifconfig br0 up
ifconfig tap0 up
route add default gw 192.168.1.1


Is that before or after running the script above?


> **Yoann Juet said:**
> 
Not sure this is really important. tap0 interface has yet been created added.

How do I create the tap0 interface?

---

### Post by Yoann Juet on 2009-11-20
> **spongypants23 said:**
> Is that before or after running the script above?

After

> How do I create the tap0 interface?

No need to create it manually. The command "openvpn --mktun --dev $t" do it for you.

---

### Post by spongypants23 on 2009-11-20
> **Yoann Juet said:**
> After



No need to create it manually. The command "openvpn --mktun --dev $t" do it for you.


I love you! It works now! :KS

Though I'm guessing these changes go away after a reboot.

Do you know how to get the computer to run the bridge script and the commands you gave me at startup, in that order?

---

### Post by Yoann Juet on 2009-11-21
> **spongypants23 said:**
> I love you! It works now! :KS

Though I'm guessing these changes go away after a reboot.

Do you know how to get the computer to run the bridge script and the commands you gave me at startup, in that order?

Great ! Now, add the following lines to your /etc/rc.local file:

/path/to/your/openvpn/script
ifconfig br0 up
ifconfig tap0 up
route add default gw 192.168.1.1

---

### Post by spongypants23 on 2009-11-21
Many thanks! :D

---

