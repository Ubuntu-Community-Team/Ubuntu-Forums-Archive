---
title: "LAN IP listing issue"
date: 2012-08-05
forum: Networking &amp; Wireless
---

### Post by FerasMoalla on 2012-08-05
Hi

Trying to list the host's IPs connected to my LAN, using the command:

sudo arp-scan --localnet

It's not working, I get this respond:

root@localhost:~$ sudo arp-scan --localnet
ioctl: Cannot assign requested address
WARNING: Could not obtain IP address for interface eth0. Using 0.0.0.0 for
the source address, which is probably not what you want.
Either configure eth0 with an IP address, or manually specify the address
with the --arpspa option.
Interface: eth0, datalink type: EN10MB (Ethernet)
ERROR: Could not obtain interface IP address and netmask
ERROR: pcap_lookupnet: eth0: no IPv4 address assigned

I am connected to the internet using wlan0 interface and not eth0, why is it talking about eth0 here? any suggestions?

---

### Post by Iowan on 2012-08-05
Dunno if this will help:
> --localnet or -l
    Generate addresses from network interface configuration Use the network interface IP address and network mask to generate the list of target host addresses. The list will include the network and broadcast addresses, so an interface address of 10.0.0.1 with netmask 255.255.255.0 would generate 256 target hosts from 10.0.0.0 to 10.0.0.255 inclusive. If you use this option, you cannot specify the --file option or specify any target hosts on the command line. [COLOR="Blue"]The interface specifications are taken from the interface that arp-scan will use, which can be changed with the --interface option.[/COLOR] 

---

### Post by FerasMoalla on 2012-08-05
> **Iowan said:**
> Dunno if this will help:

It helped, this command worked;

sudo arp-scan -interface wlan0 --localnet

Thanks

---

