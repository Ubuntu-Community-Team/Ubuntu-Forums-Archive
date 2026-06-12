---
title: "Default blocked ports on Kubuntu"
date: 2011-10-21
forum: Networking &amp; Wireless
---

### Post by MIssigno on 2011-10-21
Hi there!

I have recently moved from Ubuntu to Kubuntu... to find out that K is blocking some esscensial wireless ports! (World of Warcraft ports).

So... How may i change this? I tried firestarter... but altough it showed that WoW was trying to reach port 1119; those policies didnt do anything.

Any insights would be very very welcome.


Thanks in advance!

---

### Post by 2F4U on 2011-10-22
On Ubuntu and, as far as I know also on Kubuntu, there is no firewall installed by default. Are you sure that Kubuntu is blocking the port or maybe your router or ISP? In any case, if you use the default firewall, you can disable it by 

sudo ufw disable

---

### Post by lovinglinux on 2011-10-22
Firewall is installed by default, but is set to allow all connections. Firestarter is just a Firewall manager, that allows you to easily create firewall (iptables) rules.

I do not recommend Firestarter. Remove it and install Gufw, which is the GUI for the default firewall manager, known as UFW.

Keep in mind that you not necessarily need a firewall. Most likely you don't. Although Ubuntu comes with no firewall blocking rule by default, all ports are actually closed, because a port is only open when there is an application listening to the port. This means that even if a computer on the network is capable of reaching your machine, it won't be able to do anything, because there is no applications listening to any ports. When you launch a multiplayer game or a torrent client for example, they indeed open some ports. You don't need a firewall to block those ports either, otherwise you won't be able to connect to the server.

Most likely that your problem is because you didn't forward the ports on the router. Using a router is another reason why you most likely don't need a firewall on your machine, since most routers come with a firewall and won't allow unrequested connections to reach your machine, unless you forward some ports to your machine.

---

### Post by haqking on 2011-10-22
> **lovinglinux said:**
> Firewall is installed by default, but is set to allow all connections. Firestarter is just a Firewall manager, that allows you to easily create firewall (iptables) rules.

I do not recommend Firestarter. Remove it and install Gufw, which is the GUI for the default firewall manager, known as UFW.

Keep in mind that you not necessarily need a firewall. Most likely you don't. Although Ubuntu comes with no firewall blocking rule by default, all ports are actually closed, because a port is only open when there is an application listening to the port. This means that even if a computer on the network is capable of reaching your machine, it won't be able to do anything, because there is no applications listening to any ports. When you launch a multiplayer game or a torrent client for example, they indeed open some ports. You don't need a firewall to block those ports either, otherwise you won't be able to connect to the server.

Most likely that your problem is because you didn't forward the ports on the router. Using a router is another reason why you most likely don't need a firewall on your machine, since most routers come with a firewall and won't allow unrequested connections to reach your machine, unless you forward some ports to your machine.

+1

All ports are essentially closed as there are no services listening on them by default.

Firestarter is out of date and buggy so not recommended and the firewall is netfilter which is hardcoded into the Linux kernel and all firewall interfaces manipulate IPTables which is what configures netfilter.

As mentioned above it is likely port forwarding is not setup or not set up correctly

---

### Post by MIssigno on 2011-10-22
First of all, thanks all for your interesting answers.

I dont think my router is blocking the games ports; because I have double boot and on the windows side WoW is running perfectly.

Ill try Gufw and see if there is anything that I can do from there.

I really dont need a firewall; and I dont really want it. I was installing them just for seeing if the problem was over there.

If not... Maybe Wine is blocking my connection somehow? 

The problem, specificaly, is that when WoW is Connecting (and reaching port 1119, according to firestarter), it fails, and a "You have been disconected from server" message appears. I didnt have this problem on Ubuntu, on the same machine and router and partition.

---

### Post by MIssigno on 2011-10-22
Finnally! Got the solution:

Using native wininet: 
```
wget kegel.com/wine/winetricks 
sh winetricks wininet 
```

Was a thing of Wine after all... Thank you guys! =D

---

