---
title: "Block all access to the internet"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by thecapsaicinkid on 2011-10-11
I'm after a terminal command that will temporarily block all traffic to the internet (but still allow traffic internally) and obviously a command to restore it again. Any suggestions?

Maybe replace the dns with a bogus value?

---

### Post by chili555 on 2011-10-11
That's certainly an option. ```
sudo su
echo "nameserver 0.0.0.0" > /etc/resolv.conf
exit
```Restore with "nameserver 8.8.8.8" etc.

---

### Post by sanderj on 2011-10-11
> **thecapsaicinkid said:**
> I'm after a terminal command that will temporarily block all traffic to the internet (but still allow traffic internally) and obviously a command to restore it again. Any suggestions?

Maybe replace the dns with a bogus value?

You can then still access Internet based on pure IP addresses.

If you really want to block Internet, use a firewall, with a firewall GUI manager like [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by matt_symes on 2011-10-11
Hi

Another method is to delete your route to your default gateway. Take a look at this.
```

matthew@matthew-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         DD-WRT          0.0.0.0         UG    0      0        0 wlan0
matthew@matthew-laptop:~$ ping -c1 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=49 time=31.1 ms

--- 8.8.8.8 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 31.160/31.160/31.160/0.000 ms
matthew@matthew-laptop:~$ **sudo route del default**
matthew@matthew-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
matthew@matthew-laptop:~$ ping -c1 8.8.8.8
connect: Network is unreachable
matthew@matthew-laptop:~$ ping -c1 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=6.48 ms

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 6.489/6.489/6.489/0.000 ms
matthew@matthew-laptop:~$ **sudo route add default gw 192.168.1.1 wlan0**
matthew@matthew-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         DD-WRT          0.0.0.0         UG    0      0        0 wlan0
matthew@matthew-laptop:~$ ping -c1 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=49 time=27.5 ms

--- 8.8.8.8 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 27.556/27.556/27.556/0.000 ms
matthew@matthew-laptop:~$ 
```It would boil down to two commands. This would be just for your computer though.

Kind regards

---

### Post by haqking on 2011-10-11
> **sanderj said:**
> You can then still access Internet based on pure IP addresses.

If you really want to block Internet, use a firewall, with a firewall GUI manager like [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

I would agree that only resolution would cease

I would TOTALLY disagree with firestarter though as it is out of date, unsupported and bug rich ;-)

UFW if you want an interface to IPTables or GUFW if you want GUI.

if you want to block internet traffic, unplug the cable/dsl cable ;-)

or login to your router and down your WAN interface

or as above change your route

---

