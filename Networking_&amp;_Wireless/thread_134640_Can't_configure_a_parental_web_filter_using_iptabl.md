---
title: "Can't configure a parental web filter using iptables, squid and dansguardian"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by SmartWarthog on 2006-02-22
Hi,

I am trying to set a web content filtering system based on [[COLOR="Blue"]this article I found[/COLOR]]("http://www.linux.com/print.pl?sid=04/07/01/1833212") on a fresh Ubuntu 5.10 installation.

I installed dansguardian and squid packages using Synaptic and it went well until the saving firewall rules part. When I gave the "iptables-save > /etc/sysconfig/iptables" command, it said that file/directory didn't exist! Then I created the dir and the file iptables and put the "iptables-save" output into that file. However, when I try to perform the commands:

```
chkconfig squid on
chkconfig dansguardian on
service squid restart
service dansguardian restart
```

It just says those commands don't exist! Have I done something wrong, is the article broken or do I have to do something else?

Can someone help me setting this thing up please?

Thanks all =)

---

### Post by harnadem on 2006-02-22
You can try using the following commands to restart the services:

sudo /etc/init.d/squid restart
sudo /etc/init.d/dansguardian restart  

I believe that they will work.  Sorry, but am not in front of my breezy box and can't remember what replaces the chkconfig commands. Someone else on this group should be able to help with that.  Good luck!

---

