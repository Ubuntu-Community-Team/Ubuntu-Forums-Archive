---
title: "Help needed: Getting traffic in bytes per user from PCAP file?"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by RaginRob on 2011-02-01
Hi all,
 
my boss told me to analyze our network traffic to find out which local  user (resp. workstation) downloads how much from the internet. Not for  any obscure Big Brother purposes ;-) just to get an overview of the needs of our users (there are 14) and as a basis for a future line upgrade.
 
So I set up a linux box with 3 NICs and established a bridge br0 with  eth0 and eth1, eth2 just to access the box via ssh. Then placed this box  between our main switch and our internet gateway. It works flawlessly  and is completely transparent to the local network.
 
I then started tcpdump on br0 and dumped the complete traffic into a  PCAP file. The size is quite big after a day in the office, about 2.5  GB. When I try to open it in Wireshark, it takes forever and it usually  crashes before the complete PCAP gets loaded.
 
I was wondering if there is a more elegant and useful way to determine  the inbound and outbound traffic per local workstation out of a PCAP  file? I already thought of first reading out all ip addresses containing  192.168. from the big PCAP, then extract new PCAP's from the big one,  one per local IP, then measure the bytes in that files. That's a lot of  work.. and I'm almost sure there's some better way to do it?
 
Thanks for your help!
 
Regards, Rob

---

