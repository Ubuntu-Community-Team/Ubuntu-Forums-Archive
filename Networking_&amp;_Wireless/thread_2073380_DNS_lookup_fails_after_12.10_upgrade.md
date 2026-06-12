---
title: "DNS lookup fails after 12.10 upgrade"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by fourwood on 2012-10-19
I upgraded to 12.10 yesterday and now I can't seem to resolve domain names.  Connection Information seems to provide proper DNS server addresses from DHCP, but "ping" and "nslookup" both immediately fail with "unknown host" errors.  I have tried external servers (google.com, ubuntu.com) as well as internal network host names, and none work.  I can successfully ping IP addresses (internal and external).  This occurs for both ethernet and wireless connections.  Booting into Windows 7 on the same system does not have this problem.

---

### Post by freerk on 2012-10-19
Same problem; don't know what to do...

---

### Post by bmaranville on 2012-10-25
I had the same problem, noticed that /etc/resolv.conf had only 127.0.0.1 listed as a nameserver (I'm on a router connection and it should be 192.168.1.1)

I manually changed it but I'm not sure why the wireless handshake didn't set it properly, since my wifi connection shows the Primary DNS and Default Route are 192.168.1.1.

---

### Post by ORF1000 on 2012-10-26
I'm having the same problem -- or at least a similar problem.  My Windows partition still works, but not Ubuntu.  Worked OK before the upgrade to 12.10.  I'm wired only, not wireless on this box.  

I thought the loopback address was supposed to change to 127.0.1.1 with theis upgrade, but it's still 127.0.0.1 in /etc/resolv.conf.  Can that cause a problem?

I can ping other IP addresses on my network, but I can't ping outside the network.  Can't ping Google, even using their IP.

My many previous ugrades have worked fine, but this one is perplexing.  Any suggestions are appreciated.

---

### Post by ORF1000 on 2012-10-30
I'm watching [this thread]("http://ubuntuforums.org/showthread.php?p=12327654#post12327654") to see if it gets us an answer.

---

### Post by emanuelv on 2012-11-14
Hi,

I had the same issue, after upgrading from Xubuntu 12.04 to 12.10, I could not resolve domain names anymore.

I simply followed this procedure found at [http://askubuntu.com/questions/21201...er-doesnt-work]("http://askubuntu.com/questions/212013/name-resolver-doesnt-work")

   
```
sudo dpkg-reconfigure resolvconf 
```And I answered Yes to the prompts

It fixed my issue :cool:

---

### Post by jdthood on 2012-11-14
emanuelv's solution is probably the solution for most of you. Somehow resolvconf did not get installed properly and is not able to update resolv.conf. Note that if a local forwarding nameserver is running then the right address is 127.0.0.1 (Precise) or 127.0.1.1 (Quantal).

---

### Post by jdthood on 2012-11-14
> **emanuelv said:**
> 
I simply followed this procedure found at [http://askubuntu.com/questions/212013/name-resolver-doesnt-work]("http://askubuntu.com/questions/212013/name-resolver-doesnt-work") 

If that answer helped you then please vote it up. ;)

---

### Post by heke on 2012-12-22
> **emanuelv said:**
> Hi,

I had the same issue, after upgrading from Xubuntu 12.04 to 12.10, I could not resolve domain names anymore.

I simply followed this procedure found at [http://askubuntu.com/questions/21201...er-doesnt-work]("http://askubuntu.com/questions/212013/name-resolver-doesnt-work")

It fixed my issue :cool:

Yes, I too had the very same dns fault after I updated watt-os -an ubuntu derivative - to version 12.10. This procedure fixed my issue too. ):P

---

