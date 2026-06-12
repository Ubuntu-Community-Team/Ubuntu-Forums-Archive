---
title: "Packets DROPPED by firewall"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by tomveil on 2010-03-13
Hello all,

I am using ubuntu 9.10. Configuring my firewall using guarddog. 

I have setup a rule to allow traffic OUT on port 7078 UDP, and just because i'm having problems i added an IN rule. 

# Create the filter chains
# Create chain to filter traffic going from 'Internet' to 'Local'
ipchains -N f0to1
# Create chain to filter traffic going from 'Local' to 'Internet'
ipchains -N f1to0

ipchains -A f0to1 -p udp --sport 0:65535 --dport 7078:7078 -j ACCEPT
ipchains -A f1to0 -p udp --sport 7078:7078 --dport 0:65535 -j ACCEPT

ipchains -A f1to0 -p udp --sport 0:65535 --dport 7078:7078 -j ACCEPT
ipchains -A f0to1 -p udp --sport 7078:7078 --dport 0:65535 -j ACCEPT


# Create the filter chains
# Create chain to filter traffic going from 'Internet' to 'Local'
iptables -N f0to1
# Create chain to filter traffic going from 'Local' to 'Internet'
iptables -N f1to0
# Add rules to the filter chains
iptables -A f0to1 -p udp --sport 0:65535 --dport 7078:7078 -j ACCEPT
iptables -A f1to0 -p udp --sport 0:65535 --dport 7078:7078 -j ACCEPT




BUT I'm getting the following - 

Mar 13 21:14:59 myubuntu-910 kernel: [30375.643442] DROPPED IN= OUT=wlan0 SRC=192.168.1.4 DST=35.16.165.20 LEN=200 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=7078 DPT=41134 LEN=180 


Please advise,

Tom

---

### Post by tomveil on 2010-03-14
I should have said that I am trying to get a sip client (Linphone) running. The dropped packets are generated while making a call using Linphone. 

When I disable the firewall, the Linphone works correctly.

---

### Post by tomveil on 2010-03-15
Solved the problem - for anyone who is interested I added the following to the rc.firewall and executed the file


iptables -A f1to0 -p udp --sport 7078:7078 --dport 0:65535 -j ACCEPT 

This seems to be a statement that guarddog is not capable of creating/recognizing. 

Tom

---

