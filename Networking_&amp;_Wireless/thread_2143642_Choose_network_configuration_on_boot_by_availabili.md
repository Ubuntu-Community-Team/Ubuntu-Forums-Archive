---
title: "Choose network configuration on boot by availability (no NetworkManager)"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by kwilliam on 2013-05-09
I have a situation where I have a headless computer running Ubuntu 12.04 that I primarily connect to via SSH. It is headless because it is inside a robot, and connecting a monitor and keyboard are very inconvenient. It is bare-bones Ubunu installation - no X server, no NetworkManager. It currently connects to a wifi router using a configuration specified in /etc/network/interfaces. Because I connect to it using SSH, the computer uses a static IP whenever it boots. The current wifi configuration works, but I want to add support for wired connections and direct local-link ethernet connections. (Because who wants to drag a WiFi router around everywhere, and also Ethernet is more reliable, and also can be faster.)

What I want to do, but don't know how to do, is write an /etc/network/interfaces file that generates the following behavior on boot:
```
(This is pseudocode)
IF link-local connection exists:
    set up eth0 with static IP1
ELSE IF wired router connection exists:
    set up eth0 with static IP2
ELSE IF no Ethernet plugged in:
    set up wlan0 with static IP3
END
```

[link-local]("http://en.wikipedia.org/wiki/Link-local_address") is a direct computer-to-computer Ethernet connection. I don't know how to set that up. I also haven't been able to find an example demonstrating how to generate this kind of "fallback" behavior. I do not want to bridge any connections, I don't think. I think that using pre-up and post-up commands might be the key to achieving the fallback behavior, because they could run a script that check if the interface is already configured, but don't know exactly how. The robot just needs to do this network setup once on boot - it is very cheap to reboot the robot (only takes 5 seconds) so even if it is not robust to manual ifdown ifup commands that wouldn't matter. Here is my current /etc/network/interfaces file that I'm starting with:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
        address 192.168.0.23
        netmask 255.255.255.0
        gateway 192.168.0.1
        broadcast 192.168.0.255
        wpa-ssid metHubo
        wpa-psk [removed] 
        dns-nameservers 192.168.0.1

```
If someone could post a dummy /etc/network/interfaces file showing how to do the fallback from link-local to wired router to wireless router, that would be great.

---

### Post by tgalati4 on 2013-05-09
Your definition of link-local depends on your robot's ethernet jack or the connecting computer's ethernet jack to support swapping TX and RX lines.  Normally one would use a cross-over or patch cable (typically bright orange or yellow) for such a connection.  Normally you don't need a custom IP for such a connection.  So simply defining a manual IP and auto eth0 and auto wlan0 should be sufficient.  For your link-local connection, your laptop needs to have a manual IP in the same LAN subnet.

When wireless drops and wired is detected, the connection should be made automatically.  

```
man interfaces
```

Will have detail on all the settings available.

---

