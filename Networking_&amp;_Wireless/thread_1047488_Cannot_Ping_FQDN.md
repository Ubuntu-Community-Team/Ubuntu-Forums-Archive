---
title: "Cannot Ping FQDN"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by zigx on 2009-01-22
Hi Guys,

As of this morning i am unable to ping FQDNs like google.com from an Ubuntu Server.

Example:
bc@skywalker:~$ ping google.com
PING google.com (72.14.205.100) 56(84) bytes of data.

--- google.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms


My setup basically consists of eth0 and eth1 bridged to br0 and br1 respectively.  

locally i can access everything by IP no problem but once i try to get past my router its all downhill, lol.  Other ubuntu hosts on my LAN are able to get out without problem.

I have compared /etc/resolv.conf against a DHCP based WORKING system and it's identical.


Any ideas how i can debug this or where to start?!


thanks!!

---

### Post by zigx on 2009-01-22
Oh, maybe this will help... 

here is /etc/networking/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# iface eth0 inet dhcp
iface eth0 inet manual

# NIC number 2
auto eth1
# iface eth1 inet dhcp
iface eth1 inet manual

auto br0
# manual br0
iface br0 inet static
        address 192.168.0.216
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

auto br1
# manual br1
iface br1 inet static
        address 192.168.0.116
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


```


and here is my log output:

```

bc@skywalker:~$ tail -f /var/log/daemon.log 
Jan 22 10:10:01 lucca console-kit-daemon[5082]: CRITICAL: cannot initialize libpolkit 
Jan 22 10:17:01 lucca console-kit-daemon[5161]: CRITICAL: cannot initialize libpolkit 
Jan 22 10:20:01 lucca console-kit-daemon[5278]: CRITICAL: cannot initialize libpolkit 
Jan 22 10:20:42 lucca ntpdate[5425]: can't find host ntp.ubuntu.com 
Jan 22 10:20:42 lucca ntpdate[5425]: no servers can be used, exiting
Jan 22 10:20:52 lucca ntpdate[5571]: can't find host ntp.ubuntu.com 
Jan 22 10:20:52 lucca ntpdate[5571]: no servers can be used, exiting
Jan 22 10:20:53 lucca ntpdate[5621]: adjust time server 91.189.94.4 offset 0.001283 sec
Jan 22 10:21:00 lucca ntpdate[5683]: no server suitable for synchronization found
Jan 22 10:21:04 lucca console-kit-daemon[5701]: CRITICAL: cannot initialize libpolkit 
^C
bc@skywalker:~$ tail -f /var/log/syslog 
Jan 22 10:20:47 lucca kernel: [ 1755.770262] br1: port 1(eth1) entering learning state
Jan 22 10:20:48 lucca kernel: [ 1757.160006] br0: no IPv6 routers present
Jan 22 10:20:52 lucca ntpdate[5571]: can't find host ntp.ubuntu.com 
Jan 22 10:20:52 lucca ntpdate[5571]: no servers can be used, exiting
Jan 22 10:20:53 lucca ntpdate[5621]: adjust time server 91.189.94.4 offset 0.001283 sec
Jan 22 10:20:56 lucca kernel: [ 1764.770131] br1: topology change detected, propagating
Jan 22 10:20:56 lucca kernel: [ 1764.770138] br1: port 1(eth1) entering forwarding state
Jan 22 10:20:57 lucca kernel: [ 1766.130071] br1: no IPv6 routers present
Jan 22 10:21:00 lucca ntpdate[5683]: no server suitable for synchronization found
Jan 22 10:21:04 lucca console-kit-daemon[5701]: CRITICAL: cannot initialize libpolkit 
^C
bc@skywalker:~$ tail -f /var/log/debug 
Jan 22 09:52:14 lucca kernel: [   24.170043] ata_piix 0000:00:1f.5: setting latency timer to 64
Jan 22 09:52:14 lucca kernel: [   24.663836] sr 1:0:1:0: Attached scsi CD-ROM sr0
Jan 22 09:52:14 lucca kernel: [   25.048122] PM: Resume from partition 8:5
Jan 22 09:52:14 lucca kernel: [   25.048123] PM: Checking hibernation image.
Jan 22 09:52:14 lucca kernel: [   25.048270] PM: Resume from disk failed.
Jan 22 09:52:14 lucca kernel: [   43.573761] eth0: no IPv6 routers present
Jan 22 09:52:16 lucca kernel: [   45.060030] eth1: no IPv6 routers present
Jan 22 09:52:25 lucca kernel: [   54.470039] vnet0: no IPv6 routers present
Jan 22 10:20:48 lucca kernel: [ 1757.160006] br0: no IPv6 routers present
Jan 22 10:20:57 lucca kernel: [ 1766.130071] br1: no IPv6 routers present



```

---

### Post by disciple3d on 2009-06-12
Hi Zigx,

I had a similar problem - maybe this will help:

sudo /etc/init.d/avahi-daemon stop

Magically, FQDN pings and SSH connections started working after I did that.  Don't ask me what's wrong with it though... haven't got that far yet :)

Chris

---

