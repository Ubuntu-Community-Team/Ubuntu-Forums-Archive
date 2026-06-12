---
title: "Multicast in a VirtualBox LAN"
date: 2012-08-07
forum: Networking &amp; Wireless
---

### Post by Kanagi on 2012-08-07
Hello folks,

I have been tasked with setting up a LAN with virtual machines using Virtual Box.

I am using Ubuntu Server 10.04 and I am very new to Linux.

I do not have a router, so I will need to use a program like PIMD or SMCRoute.

My thought process is to set up 4 VMs:
One as a source to send multicast traffic.
One as a router (using pimd or smcroute)
Two as receiving clients

I have two network interfaces setup in each VM.  One using NAT that connects to my host machine for internet.  The second one is set to an Internal Network and I have statically assigned the IP Address' for these.

I am able to ping between all the devices.

I believe I am missing/confusing these steps:
1. Proper configuration for PIMD or SMCRoute
2. How do I have my clients join the multicast group?
3. How do I test traffic is being sent to all clients?

Could anyone offer any tips? Or am I going about this project the wrong way?

---

