---
title: "kubuntu - cannot  connect to ports"
date: 2006-04-20
forum: Networking &amp; Wireless
---

### Post by johnlon on 2006-04-20
I've installed kubuntu and have apache running, however I cannot conect to apache using a browser from the same machine apache is running on.

I can see that apache is listening on port 80 using netstat.

If I attempt to connect to apache using 
> telnet  ipaddress 80
I just get 
  Trying ....

I cannot even "ping localhost" - it just hangs.

At work I'm familiar with this sort of blocking response being due to having a firewall in the way.

iptables looks like this ... 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Do I need to make a change here to enable connections to port 80 from the local machine to the local machine?

To be honest I'm just using kubuntu for prototyping and have no interest in having a firewall installed at this time so is it possible to completely disable all security features.

A detail that may be important is that I am running kubuntu inside vmware.

Bizarrely  - I can connect to the kubuntu apache from the host operating system but from within kubuntu I cannot connect to local services?

---

### Post by johnlon on 2006-04-25
Any offers?


I've got a machine that runs services, eg http.

I can connect to those services from other machines but on the machine itself I cannot connect to any of the local services?

A wierd situation.

PLEASE HELP :-?

---

### Post by johnlon on 2006-05-03
Here's my twisted workaround.

Setup NAT on the VMWare adapter in the host OS (ie VMWare on windows).
Set NAT so that it redirects back into Ubuntu.

So to talk to local services from Ubuntu I actually direct the request at NAT on VMWare/Windows!

---

