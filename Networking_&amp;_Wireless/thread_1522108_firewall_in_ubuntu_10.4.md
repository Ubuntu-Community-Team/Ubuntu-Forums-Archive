---
title: "firewall in ubuntu 10.4"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by network prog on 2010-07-01
hello to everybody.
 
I have been writing a program in java to send UDP messages between hosts, and it works fine in windows, meaning most UDP messages pass from one host to another. when I run two intances of that program in the same host UNDER UBUNTU 10.4, it also works fine. But when I try to run two instances of that program in two different hosts, running both UBUNTU 10.4, no message passes. Is there any firewall in ubuntu 10.4 peventing messages from passing? And if so, how can I disable it? I must say that I have not configured any firewall in my ubuntu 10.4, and that one of the hosts uses ubuntu 10.4 from a startup disk on key, and not from installed ubuntu 10.4 on the hard drive.
 
thank a lot in advanced.

---

### Post by jonobr on 2010-07-02
Hello


I found the use of the phrase word "most UDP messages" a bit disconcerting....

Nonetheless, I think you need to figure whats stopping where.
Im assuming your application sets up a port to send and a port to receive in a given direction and vice versa when you change ends.
I think the best thing then is to run a network trace to figure out if the packets are getting to the wire and if they are received.
Given this is UDP and there are no acks involved in the transfer, you will need to run a simulataneous trace on both ends to ensure what is sent is received.

If you use tcpdump, you should be able to view the packets being sent so, eg if your application ran on port 7777 as an example,
on one end (host a)
run
sudo tcpdump -vvv -i any port 7777
When you confirm its being sent and recieved, i would switch it around.


That should let you know where packets are being dropped or not issued from.

The only thing that could be on your system is iptables
if you 
sudo iptables -L 
and the service is running you will get an out put similar to this

Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination

This means no rules defined, worth comparing to your system in case anything else is in there

Hope this was of use

---

