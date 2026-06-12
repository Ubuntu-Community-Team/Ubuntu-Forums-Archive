---
title: "NTOP - Trouble defining local sub-networks"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by noncentz303 on 2010-11-09
Morning Folks,

I am fairly new to linux and I am trying to setup ntop to monitor my network traffic. I installed it ok but I am having a hard time forcing ntop to define my local hosts from remote hosts.

I currently uses the subnetworks of 10.10.0.0\24, 10.10.2.0\24 .... 10.10.9.0\24, 192.168.0.0\12

From what I have read I am supposed to add a line into the file "/etc/default/ntop" that will set my subnets. I added this line.

GETOPT="-m 10.10.2.0/24,10.10.3.0/24,10.10.0.4/24,10.10.5.0/24,10.10.6.0/24,10.10.7.0/24,10.10.8.0/24,10.10.9.0/24"

When I restart ntop and view my local hosts I only see the hosts on my LAN of 10.10.0.0\24 and nothing else. The weird thing is not only do the hosts on subnets "10.10.2.0 - 10.10.9.0" not show as local but ntop seems to exclude the hosts all together. So one I add this statement they all disappear and only are shown when I delete my GETOPT switch.

Has anyone experienced this kind of issue or is it just me??

Thanks,

noncentz303

---

