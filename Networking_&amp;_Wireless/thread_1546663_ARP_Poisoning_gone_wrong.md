---
title: "ARP Poisoning gone wrong"
date: 2010-08-05
forum: Networking &amp; Wireless
---

### Post by ki4jgt on 2010-08-05
OK, I'm using a neighborhood wifi network, and am trying to show my aunt that people can see what she's doing online, everything she types in, I've arped her and accidently everyone else's. My wireless card won't connect with a windows computer in adhoc, so I'm guessing that's why everyone's internet went down until I took the arp poisoning out. No one could get it! How do I do a proper arp poison for her computer only? I know the IP address, and everything else. I have nmap, ettercap, and wireshark.

I basically used nmap -sP <IP>-<netmask>
sudo nmap -sS <IP>-<netmask> to find the open ports and everything, then I used ettercap to arp her computer.
I accidently got everyones and all network traffic stopped except to my computer. I had internet when no one else did.

What's going on? I have an atheros card.

---

