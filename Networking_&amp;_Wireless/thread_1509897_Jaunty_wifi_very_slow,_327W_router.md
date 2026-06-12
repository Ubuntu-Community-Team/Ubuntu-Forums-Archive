---
title: "Jaunty wifi very slow, 327W router"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by Rishkaa on 2010-06-14
I was introduced to Ubuntu about a year ago and recently decided to come back to using the OS. I now dual boot it with Windows XP Home. My former setup was with Wubi but now I have it installed on an actual partition. (The Wubi install, for whatever reason, had little internet problems.)  

I use wireless internet, and though my network card was recognized out of the box and can connect to my network, the Internet is very slow. It takes almost a minute to look up Google. Also, Firefox will often report that it cannot find the server for whatever website I try to look up, after trying to connect to it/look it up. I also cannot access the web configuration page for my router. (192.168.1.1). The network app reports that I often have a signal strength of 40% or lower.  The following is my hardware/internet:
 
Ubuntu 9.04 Jaunty
 TrendNet TEW-424UB adapter (54mbps) 
Westell VersaLink 327W router 
ISP: CenturyTel/CenturyLink High speed internet (512kbps) 
I am the only Linux computer on my network. 

(There is no encryption on my network. I know there should be. but my parents are not very computer literate and they are the ones who have access to the network. It is easier just to go without.)  

I have tried disabling ipv6, setting custom DNS server names under ipv4, and setting the wlan rate (or something similar) to 1492. Nothing works.  This does not seem to be a network problem because my internet works fine in Windows, and I can access the configuration page for my router to change channels, PPP, etc.. 

I can't do anything involving the physical router or the DSL line because I have no access to those things.  If you need any additional information I will do my best to provide it. I would appreciate any help on the matter. Thank you.

---

### Post by Rishkaa on 2010-06-15
Fixed.

Had a Linux savvy friend help me. Apparently I needed to go find the IP of my ISP's DNS servers and make that a nameserver in /etc/resolv.conf. Signal is still bad but that is to be expected.

---

