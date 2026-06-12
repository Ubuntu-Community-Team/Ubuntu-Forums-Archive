---
title: "kernel 2.6.32-25 breaks my internet conectivity"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by MTO on 2010-10-01
Hello,
ever since Ubuntu upgraded to kernel 2.6.32-25, my wifi internet connection is terrible. It works, but constantly gives errors and connections fail. wifi strength is good, that's not the problem, it just seems internet is terrible, I was blaming my ISP until I rebooted into windows and it had no problem, then found the problem also disappeared the previous kernel. 

When I reboot and select the 2.6.32-24 kernel, internet is perfect, works as expected. No more connection issues. 

My hardware:
description: Wireless interface
product: AR9285 Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.

Thanks

---

### Post by wbruc on 2010-10-01
I have problem with my network connectivity after automatic upgrade to kernel 2.6.32-25. First, this upgrade automatically remove my wicd installation, which was installed previously to bypass terrible network problems of ubuntu 10.04 with its default NetworkManager. Now after I manually reinstall wicd, the network is still extremely slow. Reboot back to 2.6.32-24 kernel does not solve the problem.

My other computer not yet upgraded, still using 2.6.32-24, has no problem with networking, using wicd.

I wish that Ubuntu 10.04 does not end the favorable long-term record of stability of Ubuntu! What has happened lately to the team?

---

### Post by MTO on 2010-10-05
The problem persists... using prior kernel I am having no issues, but it worries me as I guess next Ubuntu 10.10 will come with latest kernel and have the same problems without being able to reboot back into kernel 2.6.32-24

What I have noticed is this:
 - Internet works ok, at times. 
 - Then, suddenly, some website, ftp,or domain stops loading.
 - Loads after minutes or retries.
 - Slow connection to those error sites.

Booting in prior kernel does not have this issue. What's going on?
Thanks

---

### Post by desnaike on 2010-10-05
I had the same problem I reinstalled the drivers worked for me.

---

### Post by MTO on 2010-10-08
Problem solved reinstalling drivers.

In my case:
[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

---

### Post by patrolman on 2010-11-01
> **MTO said:**
> Problem solved reinstalling drivers.

In my case:
[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)This seems to have worked for me too thanks a lot! The problem was getting more and more irritating.

---

