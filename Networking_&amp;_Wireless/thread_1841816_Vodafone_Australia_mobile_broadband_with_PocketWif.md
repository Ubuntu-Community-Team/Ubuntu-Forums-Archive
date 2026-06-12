---
title: "Vodafone Australia mobile broadband with PocketWifi unusable"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by waitem on 2011-09-10
About two weeks ago, having previously worked fine, my connection from my Ubuntu 11.04 laptop to Vodafone Australia using a PocketWifi device (Huawei E585 version 1026.11.84.05.503sp04) suddenly became almost unusable.

Symptoms were that it was almost impossible to surf any websites, pick up or send e-mails. If I was lucky enough to make a connection, chances were that it would then timeout when I tried to do anything. There were many "server not found" messages.

I initially suspected that Vodafone had changed something in their network because everything had previously worked fine. Indeed Vodafone are in the process of "improving" their network coverage here. Calls to the Vodafone helpdesk got the standard responses of "reset the PocketWifi" and "you don't have a very strong signal where you live".  So I got in the car and tried making connections an area where I knew that Vodafone had a strong signal. The result was hardly any better.

After two weeks of frustration and just about to cancel my contract with Vodafone, I then started to investigate why there were so many DNS resolution problems and after manually putting a few "favourite" entries into /etc/hosts found the following article [http://jbolos.com/2011/07/speeding-up-internet-browsing-on-linux-using-pdnsd-for-persistent-dns-caching/](http://jbolos.com/2011/07/speeding-up-internet-browsing-on-linux-using-pdnsd-for-persistent-dns-caching/)

Quick tests showed that after changing resolv.conf to use one of the OpenDNS servers (e.g. 208.67.222.222) the performance was suddenly massively better.

In the end, the solution that I implemented was a simpler version of the one in the article above:

1. Install pdnsd (resolvconf is automatically installed with it):
   sudo apt-get install pdnsd

2. Modify my wireless connection to the PocketWifi in Network Manager under the IPv4 settings:
   Change "Method:" to "Automatic (DHCP) addresses only"
   In "DNS Servers" insert the Pocketwifi, OpenDNS and Google DNS server IP addresses:
      192.168.1.1, 208.67.222.222, 208.67.220.220, 8.8.8.8, 8.8.4.4
(Note that I deliberately let the pdnsd/resolvconf DNS cache use the PocketWifi (192.168.1.1) as the first DNS server (which in turn picks up the  Vodafone DNS servers) to avoid unnecessarily stressing the OpenDNS and  Google DNS servers when pdnsd needs to resolve a new address.)

3. Reboot (so that pdnsd/resolvconf start using the new DNS servers)

After that, massively improved broadband performance.

I conclude that Vodafone, in upgrading their network, have done something that has significantly worsened their DNS server response times.

This solution has worked for me, hence I have posted this article in the hope that others may benefit from my experience.

---

