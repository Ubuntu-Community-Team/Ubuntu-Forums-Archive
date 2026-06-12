---
title: "ubuntu 9.10 network connection issues"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by xzenox on 2009-11-14
This post is a duplicate from: [http://superuser.com/questions/70544/ubuntu-9-10-network-connection-issues](http://superuser.com/questions/70544/ubuntu-9-10-network-connection-issues)
This is to increase visibility, I will edit both posts when I have an answer/fix.

-------
                 Hi, I was previously using 9.04 fine (and in fact, I am posting this from my old 9.04 live cd). I tested the following install steps in a virtualbox vm prior to following the sames ones to upgrade my laptop:
- Download/burn ubuntu minimal cd (12mb one)
- Install ubuntu minimal
- sudo apt-get update
- sudo apt-get upgrade
- sudo apt-get ubuntu-desktop ubuntu-standard


  In the VM worked fine and I found myself with a working 9.10 ubuntu, network worked fine and I was able to test my backups and DropBox without a hitch (host was 9.04). 



When I followed the same steps on my laptop, everything worked up to after 9.10 being installed and working. As far as I can tell, everything besides eth0/wireless works.
  For some reason, I am unable to access the internet. Ping reports that over 99% of packets get lost (over an hour or so of pinging). This means for example that if I try hard enough, I can load a webpage but only at the cost of much patience... This happens both for a wired and wireless connection to my wrt310n (updated with latest firmware). At first I thought that it could be related to the ipv6 issues ppl have been experiencing however even after disabling ipv6 at the kernel level (through grub), I still get the issue. I do not think this is related to DNS issues or the likes since even when I ping my ISP's gateway IP, I have the same amount of packet loss. No DNS resolving should be required there. Access to my router works peachy with no packet loss there. I've tried different MTU values but to no avail.
  

Note that this issue affects every web-enabled application: firefox, ping, synaptic, etc. The same hardware/router combo works with 9.04 but not with 9.10. In fact, when I did: sudo apt-get ubuntu-desktop ubuntu-standard after 9.10 minimal was installed, it downloaded over 400mb of packages without a hitch so my guess is that one of those packages either in ubuntu-desktop or ubuntu-standard is causing havok.
  

Thoughts? Please help :(

---

### Post by xzenox on 2009-11-15
I finally managed to download wicd with much pain and patience and I'm happy to report it is much better now. It works good enough to browse the web and post this although it is too early to say it's it is back 100%. The problem must have been with the network manager package.

---

