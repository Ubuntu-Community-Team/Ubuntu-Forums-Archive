---
title: "Emulate DynDNS with Ubuntu on AWS"
date: 2013-08-18
forum: Networking &amp; Wireless
---

### Post by carn1x on 2013-08-18
I would like to emulate DynDNS using my existing 12.04 Ubuntu instance in AWS. Is there existing packages or methods to perform this? I'm very comfortable in a command line environment, however DNS management is something I've really never gone into very deep. Thanks for any tips or advice towards achieving this.

---

### Post by TheFu on 2013-08-18
Can you clarify a little?  
You want to provide external sub-domains for others?    a.example.com--> 6.6.6.1; b.example.com --> 7.7.7.1,  c.example.com --> 8.8.8.1
Or you want to update your real DNS service should your host IP change? ... you have a static DNS service, but want to treat it like a DDNS.
Or you want to provide DHCP reserved IPs and DNS for internal systems? - unlikely, since this is at AWS.
Or do you want to accept any subdomain request and redirect it to a single IP?  like a wildcard *.example.com --> 6.6.6.6

Running a secure DNS on the internet is not easy. There are DNS specific attacks these days and it is easy to bring down a small service or hack it if not run by highly skilled DNS experts.  To get started, buy the O'Reilly book on DNS and Bind - the Grasshopper book.  Be certain to read up on DNSSEC and DNS spoofing and reflection attacks - UDP makes this easy.

Out of curiosity, I googled a bit:
* [http://ubuntuforums.org/showthread.php?t=762515](http://ubuntuforums.org/showthread.php?t=762515)
* [https://www.google.com/search?client=ubuntu&channel=fs&q=ddns+running&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=ddns+running&ie=utf-8&oe=utf-8)
* [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS) ... might be just what you want.

I used to run DNS on the internet in the early 2000s. Got hacked. Stopped doing it. Decided it was better to pay experts $20/yr. It is much harder these days.  Running an internal DNS is not that hard, so whatever you do, test it internally first.

A friend's DNS server is being attacked constantly from around the world. Botnets. There isn't anything he can do except to relocate the service and change DNS names. His small company is a target for various reasons.

I wish you luck.

---

### Post by carn1x on 2013-08-18
Thanks for the info, sorry I haven't explained myself well, I'll clarify:

I have a file server at home, with a dynamic IP assigned by ISP. Currently I have a cron jon on the file server that runs periodically, checking the IP of a free DynDNS domain. If the IP does not match the ISP assigned IP, then my file server contacts DynDNS to update the dynamic IP associated with the DynDNS domain. Hence at almost any time, I can connect to the DynDNS domain from any location outside of my File Server's private network, and arrive at the public IP address of my File Server, across the public internet. No part of this process here is related to internal / private network connectivity, it's all public.

As DynDNS are moving to a paid model (and why shouldn't they) and the free option is becoming more and more restricted, I thought this could be something I could host on my rather under utilized Ubuntu AWS instance and cut out DynDNS from the process. I'm not sure if this constitutes a traditional DNS Server. Traditionally I only ever connect to my File Server via SSH and HTTP, if that has any relation.

Sorry if the above is patronising at all, didn't want to miss any details the second time round :). And thanks!

---

### Post by TheFu on 2013-08-18
> **carn1x said:**
> Thanks for the info, sorry I haven't explained myself well, I'll clarify:

I have a file server at home, with a dynamic IP assigned by ISP. Currently I have a cron jon on the file server that runs periodically, checking the IP of a free DynDNS domain. If the IP does not match the ISP assigned IP, then my file server contacts DynDNS to update the dynamic IP associated with the DynDNS domain. Hence at almost any time, I can connect to the DynDNS domain from any location outside of my File Server's private network, and arrive at the public IP address of my File Server, across the public internet, nothing here is related to internal / private networking.

As DynDNS are moving to a paid model (and why shouldn't they) and the free option is becoming more and more restricted, I thought this could be something I could host on my rather under utilized Ubuntu AWS instance and cut out DynDNS from the process. I'm not sure if this constitutes a traditional DNS Server. Traditionally I only ever connect to my File Server via SSH and HTTP, if that has any relation.

Sorry if the above is patronising at all, didn't want to miss any details the second time round :). And thanks!

That is a **perfect description** and extremely valid use case.  DNS is really just 3 config files.  Modifying them shouldn't be any issue.  If you know that your IP doesn't change too frequently, you can reduce the load by controlling the TTL for the DNS refreshes.  If you know the IP will change, then you can set that to 5 minutes.  I have mine set to once a day.  Scripting the changes for the files and sending the "-HUP" signal to the bind process (tells it to reread the config files), will be easy.  From your client machine, I'd script a connection to my router and ask what my public IP is, then use rsync over ssh to push that address to the remote server, but only if it has changed. That way, if the remote file hasn't changed, then you don't need to HUP the bind service.

None of this is hard.  bash, sed should be it.  Python would be overkill, IMHO. You will manually setup Bind the first time, then use sed to modify the 2 config files only when necessary.  A few 1-5 line scripts - that's all.  If you look at this: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto) you can see how easy the sed scripts will be.

Oops - I forgot - don't forget to increase the serial number for each update. This is how other DNS servers that cache the data know an update was made.

Do you have a domain already?

---

