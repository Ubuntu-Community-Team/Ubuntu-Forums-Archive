---
title: "No internet networking connection tool"
date: 2012-11-03
forum: Networking &amp; Wireless
---

### Post by gtdcubo on 2012-11-03
On my desktop computer I have inadvertently uninstalled the part of the Ubuntu 11.10 operating system that connects to the network. I do not know what it is called but its symbol is a  a quarter circle with concentric lines which when clicked allows to connect to the network, or set up new network connections. On my laptop, where it still exists, I have tried to deduce what this may be called, but cannot give you the exact name. Anyhow, I am assuming from my description that you will recognise what I am talking about.

Is it called network manager?

What I need is this, please

How can I reinstall it from what I have locally? That is to say, as I cannot connect to the internet I shall not be able to install it with the software center or terminal session that does an apt-get via the internet. I am assuming that maybe the tool exists locally for reinstallation somehow. That said my installation is one that hs evolved from 10.04 -> 10.11 -> 11.04 -> 11.10, and I do not have an 11.10 CD or anything like that. I do not know if software and application installation files are stored locally. 

I have 11.10 on my laptop, but this is the portable computer version of Ubuntu 11.10. Is there anyway that I can port this functionality from my laptop where it is working to my PC where it is not, via a USB drive or something like that.

Actually what I was trying was the replacement of network manager with wicd and the command I used was

```
sudo apt-get remove –purge network-manager
```The fact is I was attempting to replace this tool with one called wicd, as in 11.10 many forums were pointing to this as a solution for wifi slowness. I have found more than 5 forums in which the solution is propounded to remove network manager and replace it with the wicd is the following in this order

```
sudo apt-get remove –purge network-manager
$sudo apt-get install wicd
```However as soon as the network manager was purged I lost conectivity and was not in the position to install wicd.

Basically my preference is to regain network conectivity by perhaps reinstalling network manager and then to play about with installling wicd, if I may.

In short, how do I download a network managment tool when I do not already have one in order to connect to the network and download it? It is chicken and egg or recursive or whatever.

Thanks for the attention

---

### Post by Hadaka on 2012-11-03
ok, so...how are you posting..different machine?

---

### Post by gtdcubo on 2012-11-03
> **Hadaka said:**
> ok, so...how are you posting..different machine?

Yes I am indeed posting from a different machine

---

### Post by Hadaka on 2012-11-03
Hi, looks like you are not the first to do this...this is good.

try this   
[http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection](http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection)

code: arch
 to determine 32 or 64 bit

---

### Post by gtdcubo on 2012-11-03
> **Hadaka said:**
> Hi, looks like you are not the first to do this...this is good.

try this   
[http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection](http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection)

code: arch
 to determine 32 or 64 bit

This worked but let me clarify. In this link there are 4 different solutions mentioned in the link. The one that worked for me is the first which is to download the package and port it to the affected machine on a USB dirive. I tired two of the other three solutions and they did not work. The one I did not try was the one applying to 12.04.

In the future I would recommend using the first solution on this link and ignoring the others. Remember to download the package for the correct version of Ubuntu.

---

### Post by gtdcubo on 2012-11-03
By the way, thanks Hadaka for including the link that eventually solved this problem

---

