---
title: "Update (19 August) Hosed my DNS"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by Steve.the.Goolie on 2010-08-20
Hi All,

After restarting my computer following the 19th August update, I had no internet connection. As I could ping any IP address anywhere, it was obvious that it was a DNS problem.
I entered all of my setting into network manager (I use a manual configuration) including DNS server addresses, but this failed to correct the problem.
I rebooted my machine into windows and everything worked fine, so definitely an Ubuntu problem.
After much searching, I found a bug report on launchpad describing a bug where network manager would not update the /etc/resolv.conf file with nameserver information.
I inspected my /etc/resolv.conf file and found it was, indeed empty.

Adding the lines:

nameserver 212.139.132.56
nameserver 212.139.132.57

solved the problem. (these addresses are my ISP's nameservers, replace them with those of your choice)

Hope this may help someone in a similar situation.

Steve

---

### Post by DrMelon on 2010-08-20
My router handles my DNS stuff, so this didn't affect me.

---

### Post by Steve.the.Goolie on 2010-08-21
2.6.32-24 kernel update fixes the problem without having to enter DNS servers manually in /etc/resolv.conf

---

