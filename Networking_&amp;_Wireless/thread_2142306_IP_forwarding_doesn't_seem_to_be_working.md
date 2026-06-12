---
title: "IP forwarding doesn't seem to be working"
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by ShadowAS1 on 2013-05-05
Hello,
I'm trying to setup an L2TP/IPSec VPN which requires IP fowarding.
I've tried to enable it by issuing the following commands but ipsec (openswan) doesn't seem to like it:


```

iptables --table nat --append POSTROUTING --jump MASQUERADE
echo "net.ipv4.ip_forward = 1" |  tee -a /etc/sysctl.conf
echo "net.ipv4.conf.all.accept_redirects = 0" |  tee -a /etc/sysctl.conf
echo "net.ipv4.conf.all.send_redirects = 0" |  tee -a /etc/sysctl.conf
for vpn in /proc/sys/net/ipv4/conf/*; do echo 0 > $vpn/accept_redirects; echo 0 > $vpn/send_redirects; done 
sysctl -p

```[COLOR=inherit][FONT=Monaco]
[/FONT][/COLOR][FONT=Monaco][FONT=arial]After doing that the command: *ipsec verify* gives the following output:[/FONT][/FONT][COLOR=inherit][FONT=Monaco]
[/FONT][/COLOR]
Two or more interfaces found, checking IP forwarding            [FAILED]



Now my system is setup as follows:

Dedicated Server hosted at OVH (France) running VMWare ESXi 5.1
It has 2 NICs, one of them uses a public IP, and the other is attached to the internal LAN.
Now, the thing i'm suspecting are the weird IP Settings OVH uses.

This is my /etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo eth0
iface lo inet loopback


# eth0 (public IP, VPN host)
# Refer to http://help.ovh.ie/BridgeClient for OVH stuff
iface eth0 inet static
address xx.xx.147.145
netmask 255.255.255.255
broadcast xx.xx.147.145
post-up route add y.yyy.165.254 dev eth0
post-up route add default gw y.yyy.165.254
post-down route del y.yyy.165.254 dev eth0
post-down route del default gw y.yyy.165.254
dns-nameservers 8.8.8.8 8.8.4.4


#eth1 Internal
iface eth1 inet dhcp



```

As you can see the setup is a bit unusual, this due to the network configuration used by OVH.

So now my question is: How can I enable IP forwarding..?

Thanks! :)

---

### Post by SeijiSensei on 2013-05-05
Changing the entries in /etc/sysctl.conf does not take effect unless you reboot.  These are kernel-level parameters that are read during boot and remain in effect throughout.

Just edit sysctl.conf manually and make your changes permanent.  Then reboot and try again.

You can make on the fly changes by changing values in /proc.  For instance, you can use the command:

```
echo '1' > /proc/sys/net/ipv4/ip_forward
```

to change that parameter temporarily.  This command has to be run with root privileges, of course.

---

