---
title: "add a host record to Ubuntu DNS server"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by Wired1979 on 2013-03-21
I'm new to Ubuntu,

We have a DNS server running v11.10 that has been in place since before I started.

What is the easiest way to add a host record for a new email server? 
mailserver.xxxxxxxxx.com  68.58.201.xx

is there a file(s) I can edit or a utility I should use?

thanks

---

### Post by chili555 on 2013-03-21
I imagine it's /etc/hosts, however, I believe the correct syntax will be like:> 127.0.0.1	localhost
127.0.1.1	myserver

68.58.201.xx mailserver.xxxxxxxxx.com 

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


---

### Post by Doug S on 2013-03-21
If it is an externally facing domain name server, then there should be two. (?)
When you say DNS, do you mean you are running bind9? Or something else? I run an internal only bind9, and I can check via:```
doug@doug-64:~$ [COLOR=#FF0000]ps[/COLOR] [COLOR=#ff0000]aux | grep named[/COLOR]
doug       366  0.0  0.0   9380   884 pts/1    S+   07:43   0:00 grep --color=auto named
bind     30381  0.0  0.8 248304 26340 ?        Ssl  Mar20   0:04 [COLOR=#ff0000]/usr/sbin/named -u bind[/COLOR]
```Now, if it is bind9 that you are running, then the related files will be in /etc/bind. And some help for modifying the files can be found in the [Ubuntu server guide]("https://help.ubuntu.com/12.10/serverguide/dns.html"). (Even though you mentioned version 11.10, the link is to the 12.10 version of the guide because of some fixes to the DNS chapter that were made since 11.10)

---

### Post by Wired1979 on 2013-03-22
> **Doug S said:**
> If it is an externally facing domain name server, then there should be two. (?)
When you say DNS, do you mean you are running bind9? Or something else? I run an internal only bind9, and I can check via:```
doug@doug-64:~$ [COLOR=#FF0000]ps[/COLOR] [COLOR=#ff0000]aux | grep named[/COLOR]
doug       366  0.0  0.0   9380   884 pts/1    S+   07:43   0:00 grep --color=auto named
bind     30381  0.0  0.8 248304 26340 ?        Ssl  Mar20   0:04 [COLOR=#ff0000]/usr/sbin/named -u bind[/COLOR]
```Now, if it is bind9 that you are running, then the related files will be in /etc/bind. And some help for modifying the files can be found in the [Ubuntu server guide]("https://help.ubuntu.com/12.10/serverguide/dns.html"). (Even though you mentioned version 11.10, the link is to the 12.10 version of the guide because of some fixes to the DNS chapter that were made since 11.10)

yes, externally facing and there is two.

i'm assuming bind9 and looking at the files in the /etc/bind folder, but I can see nothing in those files that show the current web or mail server.

---

