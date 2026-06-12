---
title: "Two dyns Name server file"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by arulnambi on 2011-12-19
HI All
  There are two files in which the dns name is specified
  1)    1)  in /etc/network/interfaces
  2)    2)  in /etc/resolv.con
  Which one is the right one and what is the difference between both of them?
  Thanks a lot in adavnce for taking your time to got hrought the tutorial.
  With regards
  Arul

---

### Post by jonobr on 2011-12-19
Im not sure of the tutorial your referring to , but the interfaces file is used to define the configuration of the network interfaces.

You can define static or dynamic addresses in there as well as the loopback interface on your system.

The resolv.conf file is used to define the lcoation of the nameserver that your system will resolve to.

Resolution is done according to the setup of your /etc/nsswitch.conf file
typically it sill look to resolve using host ( the contents of the /etc/hosts file) and then dns as defined in resolv.conf.

You can also have a search domain defined in there as well.
You should either use NM applet of configuration files but not both.
The nm applet will auto-populate the contents of /etc/resolv.conf

---

### Post by arulnambi on 2011-12-20
> **jonobr said:**
> Im not sure of the tutorial your referring to , but the interfaces file is used to define the configuration of the network interfaces.

You can define static or dynamic addresses in there as well as the loopback interface on your system.

The resolv.conf file is used to define the lcoation of the nameserver that your system will resolve to.

Resolution is done according to the setup of your /etc/nsswitch.conf file
typically it sill look to resolve using host ( the contents of the /etc/hosts file) and then dns as defined in resolv.conf.

You can also have a search domain defined in there as well.
You should either use NM applet of configuration files but not both.
The nm applet will auto-populate the contents of /etc/resolv.conf
hi jonobr,
thanks a lot for your response. I was trying to set up static ip through the command line and i read that we need to specify the name server in the interfaces file. So i need not mention the nameserver in the interface file am i right?
Thanks once again
with regards
Arul

---

### Post by jonobr on 2011-12-20
Hello

The static Ip address will be defined in the /etc/network/interfaces file and the nameserver or DNS is placed into the 
/etc/resolv.conf directory not the interfaces file

The entry in the resolv.conf file is 
```
nameserver     8.8.8.8 
```
using google as an example

---

### Post by arulnambi on 2011-12-21
> **jonobr said:**
> Hello

The static Ip address will be defined in the /etc/network/interfaces file and the nameserver or DNS is placed into the 
/etc/resolv.conf directory not the interfaces file

The entry in the resolv.conf file is 
```
nameserver     8.8.8.8 
```using google as an example
Thanks for your explanation
With regards
Arul

---

### Post by jonobr on 2011-12-21
Sweet Arul

I would recommend you go to the top of the page and in the drop dowm in thread tools, mark as solved.

Lets people searching for topics like thisknow that this thread may help

Cheers

Jonobr

---

