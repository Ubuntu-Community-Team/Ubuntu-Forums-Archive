---
title: "Local DNS Setup Problems"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by AdyMareshal on 2010-05-21
I have to connect a linux installed on VMware and my Ubuntu desktop.

I have to send this command from vmware:

```
nslookup ubuntu.local
``` and I should get the IP of this domain.

How do I get started with this?

Thank you

---

### Post by bab1 on 2010-05-21
> **AdyMareshal said:**
> I have to connect a linux installed on VMware and my Ubuntu desktop.

I have to send this command from vmware:

```
nslookup ubuntu.local
``` and I should get the IP of this domain.

How do I get started with this?

Thank you

Not enough information to understand what you are trying to accomplish.  Is *ubuntu.local* the FQDN of the guest OS?  How have you provided IP addressing?  From where are you issuing the command?

---

### Post by AdyMareshal on 2010-05-21
I found this guide

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch18_:_Configuring_DNS#Basic_DNS_Testing_of_DNS_Resolution](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch18_:_Configuring_DNS#Basic_DNS_Testing_of_DNS_Resolution)

**The Host Command and The nslookup Command**

This is what I have to do. But that guide is mostly for CentOS. I need something for ubuntu. Ubuntu doesn't have "named" and bind is installed on completely different folders.

---

### Post by bab1 on 2010-05-21
> **AdyMareshal said:**
> I found this guide

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch18_:_Configuring_DNS#Basic_DNS_Testing_of_DNS_Resolution](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch18_:_Configuring_DNS#Basic_DNS_Testing_of_DNS_Resolution)

**The Host Command and The nslookup Command**

This is what I have to do. But that guide is mostly for CentOS. I need something for ubuntu. Ubuntu doesn't have "named" and bind is installed on completely different folders.

Sure it does.  See [**_here _**]("https://help.ubuntu.com/community/BIND9ServerHowto")and [**_here_**]("http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml").

---

### Post by AdyMareshal on 2010-05-23
thanks. Softpedia article works ok

---

