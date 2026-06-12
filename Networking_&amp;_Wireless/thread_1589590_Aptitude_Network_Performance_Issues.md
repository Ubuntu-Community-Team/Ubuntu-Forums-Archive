---
title: "Aptitude Network Performance Issues"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by JSpecMugen on 2010-10-06
I've searched high and low, and found a few threads that have similar issues, but found no real solution to the problem.

Here is my problem...

I'm using 10.04 LTS x86 ISO DVD to install my workstation. When the installation goes to apt-get mirrors on the web, the transfers start fast and use all available bandwidth >200kB/s then after about 10-15seconds it suddenly drops down to <2kB/s and never picks up. Unless I disable my NIC and tell Ubuntu not to look for network mirrors for Aptitude, my installation takes almost 3-4 hours.

Once I'm in the OS, everything is snappy. I can download off any site (Skype for example) and no issues in wget or Firefox. However, anything related to Aptitude exhibits the same problem. Starts out perfectly fine, and then drops back to <2kB/s. This occurs during updates/upgrades and installs.

After searching to fix the problem, some people suggested changing mirrors. So I did, and no change. Then some suggested disabling ipv6, so I did... and no change.

Also, people keep commenting me to find a better repo mirror, and while I agree that can make the difference between a 20kB/s throughput and a >1MB/s throughput... I've never seen a mirror that gives as bad a rate as <2kB/s. Especially considering these are all default mirrors that 99.999% of the people have zero issues with around the world.

Last but not least, people have said It's a FW/Router/ISP issue, but It's not. I have attempted the same installation on a desktop PC (all supported Intel everything) and Dell Vostro 1510 (All supported perfectly). I have also attempted the installation at my office on a 2mbit symmetrical wireless link, my friends Quest DSL 15mbit connection, and my house Cox@home 20x5mbit connection.

Each and every time I have run the installation, I'm presented with the same problem. It's become frustrating! I've used Ubuntu since 2.10 and never had these kind of issues.

I'd appreciate any pointers that can be sent my way, as unless I can get this situated, I will have to resume using Windows on my machines and I'd much rather not.

Regards,

Jordan W.

**UPDATED:** Trying anything I could, I decided to change my sources.list file from http:// to ftp:// and all the sites work flawlessly now at full speed. Same server I was getting 1,544bytes/s I'm now getting 287kB/s. Can someone PLEASE explain what I'm doing wrong?

**UPDATED:** Apparently the problem existed on our Adtran NetVanta 6355 firewall. It was doing some URL filtering that was inadvertently messing with certain sites.

---

