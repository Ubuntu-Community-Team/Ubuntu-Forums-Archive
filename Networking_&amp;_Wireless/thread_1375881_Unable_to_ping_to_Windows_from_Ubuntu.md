---
title: "Unable to ping to Windows from Ubuntu"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by LinuxInferno on 2010-01-08
I have am having some network troubles. I can't access my samba share. Trying to resolve this I realized I couldn't ping from ubuntu to windows. (default ubuntu.jaunty.server.x64)

Windows IP..192.168.002.021
Ubuntu IP...192.168.002.020
Laptop IP...192.168.002.031
Router IP...192.168.002.001

--Router Information
WRT54GS - DDWRT Firmware
All connections are wired with NETGEAR 1000mbps Switch

WHAT Works?
Ubuntu Ping localhost
Ubuntu Ping router
Ubuntu internet/updates
Laptop ping Windows
Laptop ping ubuntu
Windows ping ubuntu

Iptables all set to accept.
route -n is normal
/etc/hosts has 192.168.002.021 windowshostname
/etc/resolv.conf has nameserver from isp of 65.32.5.111/112
/etc/network/interfaces has properly defined static ip.


I'm confused about what to try/do next


[SOLVED] After countless hours of digging and verifying multiple times that ifconfig, route -n, nsswitch, and samba were all configured properly. I stumbled upon the answer.
All I had to do was ```
sudo aptitude remove dhcp*
```

---

### Post by LinuxInferno on 2010-01-08
I tried disabling windows firewall and microsoft security essentials. 

I also tried changing nsswitch.conf to have wins in the hosts line and adding wins to the smb.conf  -  still nothing

---

### Post by SecretCode on 2010-01-08
What OS is the laptop?

Post output of *ipconfig /all* from windows and *ifconfig* from ubuntu - and which applies from the laptop.

---

### Post by Iowan on 2010-01-08
Can Ubuntu ping Windows by address (ping -c5 192.168.002.021).

---

### Post by LinuxInferno on 2010-01-08
The laptop is OSX/Ubuntu.
BOTH sides can ping all computers.

And yet another computer with ubuntu karmic desktop x64 can ping all computers.

Iowan - I am doing all my pinging by ip
'ping -c5 192.168.002.021' replies with
"From 192.168.2.20 icmp_seq# Destination Host Unreachable
100% Packet loss

---

### Post by LinuxInferno on 2010-01-13
SOLVED! Removed DHCP packages. They seem to be conflicting with the static IP somewhere that I can't prove. IFCONFIG was correct the whole time.

---

