---
title: "Cant Put NIC in Promiscuous Mode"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by lumpie on 2010-06-17
I'm a Linux dummy. I want to monitor network traffic with ntop from a Lucid 10.04 machine. Both NICs have picked up an IP address, I need to put one in promiscuous mode. I typed** sudo ifconfig eth1 promisc** and the response was **SIOCSIFFLAGS: Permission denied**.

Any help would be appreciated

---

### Post by jonobr on 2010-06-17
Hello

Im not an ntop person but how about using wireshark in the repos?

It allows you to select hat in the Gui.
Alternatively you could use something like

```
sudo tcpdump -i eth1 -xnVVS 
```
you could also use the command port at the end to define a specific port number eg port 53 for DNS

or your could use 
```
sudo tcpdump -w trace.pcap -i eth1 -S0 
```
and view the resulting file (trace.pcap) in wireshark

---

