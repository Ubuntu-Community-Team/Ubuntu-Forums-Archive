---
title: "Cisco router or Ubuntu server"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by NoReflex on 2009-01-29
Hello!

I'm currently deciding whether to replace the router I have (Cisco 2811) with a Ubuntu server box. I'm connected to two providers (the Cisco router has two WAN interfaces) and primarily I host a jabber server and two websites. The jabber server has about 3000 connections simultaneously and there are about 30-40 people online on each website. 
I'm not Cisco certified (what I know I learned from Google) and a friend helped me set up the router. My problem with the router is that it can't help me troubleshoot an issue : if I issue the show interfaces command I get  52902 unknown protocol drops on one WAN interface (15 hours after I cleared the counters). Now I would like to know what those packets contained or where did the came from or at least what was wrong with them but I couldn't find any command that would allow me this.
I know that on Ubuntu I could use tcpdump or Wireshark to sniff the traffic and capture those packets BUT my friend told me I can't because those packets are physically dropped by the network hardware and they wouldn't get to a sniffer. 

Any ideas on how I could tackle the issue? Thanks!

Best wishes,
NoReflex

---

### Post by nixscripter on 2009-02-04
I would suggest replacing it with a real cheap Ubuntu server, yes. I'm not a fan of Cisco hardware, so I'm a little biased. ;-)


[Ubuntu and Jabber]("https://help.ubuntu.com/community/SettingUpJabberServer")
[Ubuntu as a Web Server]("http://www.tuxmachines.org/node/12638")

See if those help.

---

