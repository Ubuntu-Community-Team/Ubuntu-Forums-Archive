---
title: "can ping IPs but not names"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by jemvyc on 2012-04-04
In my small network I can ping every computer using IP address, but only the one I am working from by name.  

I have just recovered from crashing even the internet while trying to fix it.  Please help.

Jim

---

### Post by spynappels on 2012-04-04
Do you have DNS set up in your LAN? If not, have you entered each hostname with it's corresponding address in the hosts file?

Were you ever able to ping LAN hosts by hostname?

---

### Post by jemvyc on 2012-04-04
Thanks for answering.

This used to work.  I don't know why it stopped.

I have been trying to get the network set up for several days.  From network manager I have selected DHCP and tried random things, not knowing what I was doing.

The name of the computer I am using, Ubuntu-laptop is in a file /etc/hostnames  That is the computer which I can ping either via IP or name.  There is nothing else there. There are no IP addresses there.  

 The /etc/hosts looks like a spam stopper file.  Everything there has a 127.0.0.1 IP

I did not have to add names and IP addresses when this got set up before.  Would you tell me where and what syntax to put the names in?

Thanks

---

### Post by spynappels on 2012-04-05
/etc/hosts is where you define host to IP mappings on a node specific basis. This means that if you try to connect to any host by name, whether on the LAN or on the Internet, this file will be parsed to see if you have an IP address defined locally for that name.

You simply add entries in the following format in the ipv4 section:
```
aaa.bbb.ccc.ddd hostname
```  where aaa.bbb.ccc.ddd is the IP address you want to access and hostname is the hostname for that IP address, and you should then be able to use the hostname to ssh to that node.

---

### Post by hughr2005 on 2012-04-05
I believe mac implements a kind of tld for local machines. So on a mac, you can use "hostname.local" or "ubuntu-laptop.local". I've found this useful - perhaps it's time to implement this in Ubuntu.

---

### Post by jemvyc on 2012-04-05
Thanks for the help.  I put the IPs and names in the hosts file and I now see the other computers in the network.  That solves the first step.  I knew that not being able to see other computers was the main cause I couldn't print on a network printer on a windows machine.

After I have a shot at relearning how to set up samba and sharing the printer, I will probably be back here for more help.

Anyway, this issue is solved....  Thanks a bunch.

---

