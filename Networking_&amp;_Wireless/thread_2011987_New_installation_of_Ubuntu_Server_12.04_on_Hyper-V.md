---
title: "New installation of Ubuntu Server 12.04 on Hyper-V network issues"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by jvahub on 2012-06-28
Hi,
 
I've installed a new installation of Ubuntu Server x64 on one of our Hyper-V nodes. Installation was pretty straightforward, I only installed SSH server and didn't enter a proxy.
 
I havent changed much so far, the server gets its network settings through DHCP. As far as I can see that has gone well - both IP and DNS settings seem to be OK. Also gateway seems to be fine.
 
I can ping my own IP-adress (eth0), but cannot ping anything else on the internet or LAN - not even the gateway.
 
It gives the error (when pinging 10.136.51.1, I am .191):
From 10.136.51.191 icmp_seq=1 Destination Host Unreachable
From 10.136.51.191 icmp_seq=2 Destination Host Unreachable
From 10.136.51.191 icmp_seq=3 Destination Host Unreachable
 
As said earlier pinging myself works fine.
 
Other information about our network that might be useful;
- We are behind a proxy, I tried entering this before during installation but with no better results)
- We are using a domain ending with .local (which might cause some issues, although I can't see how it can cause them at this time)
- Hyper-V has Network Adapter 1 (Emulated) installed which connect to a VLAN and has virtual LAN identification enabled
- We have some other Ubuntu servers already running on Hyper-V which are doing fine (with similar NIC settings as one line above), so Hyper-V shouldn't be the problem
- Im running this installation as command line only
- We are using regular IPv4
 
I hope anyone can help me with some suggestions. Thanks in advance.
 
Best regards

---

### Post by jvahub on 2012-07-04
Just for the record, I solved this issue by assigning a different NIC within Hyper V. You have both an Emulated and Synthetic network adaptor to choose from. Make sure this is Synthetic otherwise you have the same problem as I.

---

