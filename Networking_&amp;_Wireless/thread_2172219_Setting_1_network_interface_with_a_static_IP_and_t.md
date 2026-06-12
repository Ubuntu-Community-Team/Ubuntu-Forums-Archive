---
title: "Setting 1 network interface with a static IP and the other interface as a DHCP server"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by PyPF3XL on 2013-09-03
Hello,

I am currently working on setting up a FOG server (Free Open-source Ghost) on Ubuntu 12.04 LTS 64 bit and because of specific network regulations, I am forced to set up this server a certain way. The server is a 1u box with 2 - gigabit network interfaces. A basic rundown of what I'm trying to accomplish is as follows:

- eth0 is the web interface used to manage the console of the system (Which btw we have configured to work correctly using a static IP). 
- eth1 is what we would like to have segmented from the web interface but only allow eth0 to send the necessary jobs (Deployements/Images) to this interface. This will insure that the imaging is done on a separate network (we will be connecting a small 8 port switch to eth1 to allow multiple jobs to run) and it will provide a level of security from images being compromised.

The issue I am running into I believe stems from setting up DHCP settings and the route tables as I will need eth1 to communticate to eth0 to receive the specific tasks such as deployment or imaging/cloning. I do have the DHCP server installed and I am able to configure the dhcpd.conf files and set which interface I want to handle the DCHP requests but I can't seem to get the setup right.

Any help or experience setting up a server this way would be greatly appreciated.

---

### Post by PyPF3XL on 2013-09-04
Ended up figuring this out as I had my "next-server" address and the DHCP address incorrect.

---

