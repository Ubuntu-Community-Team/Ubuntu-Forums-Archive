---
title: "1 Nic, 2 local IPs, 2 public IPs, only 1 works"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by mrryanjohnston on 2011-09-27
I'm currently maintaining a server running 10.04 LTS on a vmware server. There is currently 1 nic installed on this machine with 2 ip addresses; below is my /etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto eth0 eth0:1
iface eth0 inet static
  address 172.21.22.12
  netmask 255.255.255.0
  network 172.21.22.0
  broadcast 172.21.22.255
  gateway 172.21.22.1
iface eth0:1 inet static
  address 172.21.22.15
  netmask 255.255.255.0
  network 172.21.22.0
  broadcast 172.21.22.255
  gateway 172.21.22.1

```

The purpose of having these 2 IP addresses is to allow 2 virtualhosts in apache. These virtualhosts are set up properly; both are reachable by their local IPs from a machine in the subnet and IRC user thumbs confirmed the configuration was correct in #httpd.

There are 2 publicly facing IPs that forward to each of these local IPs in our router. The router packet manager reports as sending properly to each of these IPs. However, only 1 of these public IPs work; the first, which points to .12 works, while the IP which forwards to .15 reports as cannot connect to server.

Moreover, this problem seems to be intermittent; yesterday, with the same exact setup, both IPs worked as expected. I came back and checked the server today and neither public IP seemed to work as expected. I rebooted the virtual machine and 1 of the public IPs seemed to work while the other did not.

**EDIT:** It seems that while I was typing this message, both public IPs decided to work. I will report back if it goes down.

---

### Post by jonobr on 2011-09-27
Hello


I would recommend when its working get a tcpdump trace

then when its not get the same, and see if there is anything in the comparison of the two which may give a hint.

your tcpdump command could be

```
tcpdump -w goodtrace.pcap -i eth0:1 -s 1600 
```
when its not 
```
tcpdump -w badtrace.pcap -i eth0:1 -s 1600 
```
You can add in proto fields and source and destination ip addresses to refine your trace.

the goodtrace.pcap should be viewable on wireshark when you take it off the server.

Lastly, eth0:1 is a guess, I'm not sure that will work (tracing on a plumbed interface) if it doesn't, maybe just use eth0 see whta happens

---

### Post by mrryanjohnston on 2011-09-28
> **jonobr said:**
> Hello


I would recommend when its working get a tcpdump trace

then when its not get the same, and see if there is anything in the comparison of the two which may give a hint.

your tcpdump command could be

```
tcpdump -w goodtrace.pcap -i eth0:1 -s 1600 
```
when its not 
```
tcpdump -w badtrace.pcap -i eth0:1 -s 1600 
```
You can add in proto fields and source and destination ip addresses to refine your trace.

the goodtrace.pcap should be viewable on wireshark when you take it off the server.

Lastly, eth0:1 is a guess, I'm not sure that will work (tracing on a plumbed interface) if it doesn't, maybe just use eth0 see whta happens

Awesome. I will use this. Thanks!

---

