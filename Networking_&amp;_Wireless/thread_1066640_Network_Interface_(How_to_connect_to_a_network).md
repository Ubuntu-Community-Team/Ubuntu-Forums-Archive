---
title: "Network Interface (How to connect to a network)"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by sim085 on 2009-02-11
Hi,

I have a minor problem. I have installed Ubuntu 8.10 server edition. However I cannot connect to the network I am in. I used the command netstat –i to list any network interfaces and the result I get is the following: 

Kernel	Interface table
Iface	MTU Met	…
lo	16436		… (all zeros)
RU

This I assume means that I do have a network interface available. So is there any command which I can use to actually connect/use this network interface?

Thanks and Regards,
Sim085

---

### Post by superprash2003 on 2009-02-11
is this a wired or wireless network what does **ifconfig** show you?

---

### Post by Iowan on 2009-02-11
You can check all interfaces (even inactive ones) with **ifconfig -a**. Also, **lshw -C network** will leet you know if the interface is getting an alias (like eth0).  Besides wired/wireless, is server set for address via DHCP or for a static IP?

---

### Post by sim085 on 2009-02-12
Hi again,

I did some research over the Internet and did manage this problem. This version of Ubuntu was installed on Virtual Box. Now this allows you to define different Network Adapters. The first time I set this I got the Network Adapter eth0 and everything worked find.

However using ifconfig -a I found out that the Network Adapter I have (although new it was set up exactly as before) was labeled as eth4. I found the file /etc/udev/70-persistent-net.rules and removed all its contents. Then I restarted the virtual machine. When back up this file was updated with the a new Network Adapter labeled as eth0... and I was connected to the Internet automatically!!

So my question now is; how come, considering that the Network Adapters eth0 and eth4 where exactly the same, I was connected to the Internet automatically with eth0 but not eth4? Also while having eth4 defined I could not connect to eth0 using the ifconfig eth0 up. 

However I still have to do more research on this. I believe I made a mass out of the Network Adapters and I will try to experiment more on the topic this evening.

Thanks :)

---

