---
title: "Ubuntu not taking ARP request/answers into account"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by Ekyrby on 2012-04-27
Hello all,

I have a strange problem on a small network of mine.

It's composed of 2 machines and a switch.

PC1 is Ubuntu 9.04 (old I know) with IP 192.168.10.11. It is connected to PC2 through a switch (both machines are belonging to the same VLAN).

PC2 is Windows Seven with IP 192.168.10.1.

Both machines cannot ping each other. A bit of wireshark showed me a strange behaviour in the ARP protocol.

Ping from PC 1 (ubuntu) creates an ARP request that is received and answered by the PC2. The answered however is not taken into account by PC1 : i'm still still unable to ping 

```
From 192.168.10.11 icmp_seq=58764 Destination Host Unreachable
From 192.168.10.11 icmp_seq=58765 Destination Host Unreachable
From 192.168.10.11 icmp_seq=58766 Destination Host Unreachable
```And the ARP cache is not "complete":

```
satem@satem-desktop:~$ arp -a
? (192.168.10.1) à <incomplet> sur eth1
```On the other hand, pings from the PC2 generate ARP requests that reach PC1 but are not answered nor taken into account into the ARP cache of PC1.

Removing the VLAN tagging seems to solve the problem but I can't see why it would cause a problem (and I can't afford to remove it permanently). Also sysctl parameters arp_filter and rp_filter have been set to 0 with no apparent effects.


Thank you for your help.

---

### Post by Ekyrby on 2012-04-27
Update: after additional tests, the result is still the same when 9.04 is replaced by 11.10.

Also, I noticed that the ARP request/answers received by the PC1 (Ubuntu machine) are still VLAN tagged. On the other hand, the Windows machine gets untagged packets.

Also, same configuration with Windows Only machines works perfectly fine.

---

### Post by Cydney on 2012-05-14
Have the same problem when trying to create a hotspot with hostap and isc-dhcp-server.My Symbian phone gets IP but thats all.
I'm desperate can't find solution nowhere.

Sorry to bother

---

### Post by roelforg on 2012-05-14
@Ekyrby
What is it you're trying to do?
You could try using a proper router. (if the switch is a managed one, i think it is since you're talking about vlans, it usually has one build in, that mode usually enables when it boots w/o anything connected to it)
I think the windows<->windows combi enables some custom/propriatary protocol and
windows<->ubuntu misses that, thus disabling the network.
 
@Cydney
Enable ipforwarding.
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
```

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

```

---

