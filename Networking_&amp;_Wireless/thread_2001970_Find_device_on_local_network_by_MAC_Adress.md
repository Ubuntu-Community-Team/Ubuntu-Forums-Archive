---
title: "Find device on local network by MAC Adress"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by bakegoodz on 2012-06-11
How do I find the IP address on a local wired network by mac address with Linux. It seems like Linux would have this command, because it is easy to do in the command in Windows: arp -s 10.2.2.249 01-00-5e-7f-ff-fa

I've tried "arping", but I can't figure out syntax that works or find an example online.

---

### Post by steeldriver on 2012-06-12
I don't know if this is a 'good' way to to it, but 'nmap -n' appears to give the info you want - only if you run it as root though, e.g.

```
sudo nmap -nsP 10.2.2.249/24 
```will list all the IPs + MACs on the 8-bit host space including 10.2.2.249 ( I'm assuming you don't really want to scan the whole 24-bit 10.x.x.x/8 host space)

or 

```
sudo nmap -nsP 10.2.2.249/24 | grep -B2 01-00-5e-7f-ff-fa
```to grep out a single MAC

---

### Post by bakegoodz on 2012-06-12
I think some would be confused by the Windows command I posted. The command modifys the arp cache to assign a (bogus) IP to a MAC address of that device can be reached by my machine by that assigned IP. I really don't like explaining why I do something because it often detracts from the question. In brief, I often need to find an embedded device on a large lan. I can then ssh to the arp assigned IP then find out the devices real IP. I want to use my own Ubuntu computer to do this and not have to hunt down and borrow a Windows computer every time. I've looked at the manual for 'arp' on linux and I don't see how to do the same thing.

---

### Post by bakegoodz on 2012-06-12
Nope scanning won't work with the 65000 addresses in the address space, and a few other issues with scanning. Last time I tried I set off the intrusion detection system and got in big trouble. Save your questions, nothing I can do about it, I'm not the net admin.

---

### Post by Cheesehead on 2012-06-12
Try 'arp -n' or 'arp -a' to get IP addresses instead of machine names.
This command will give you the real IP address,
Assuming, of course, that the machine is already in your arp cache.

For example,
```
$ arp -n | grep 00:1e:c2:ab:d3:f1 | cut -d' ' -f1
192.168.1.11

$ arp -a | grep 00:1e:c2:ab:d3:f1 | cut -d' ' -f2
(192.168.1.11)
```

'arp -s' should create a new entry, just like your current method, and with identical syntax.

---

### Post by bakegoodz on 2012-06-12
Nope not it arp cache because I haven't connected to it yet.

---

### Post by The Cog on 2012-06-12
arp -s works on linux. 
You need admin rights, so use sudo.
Use colons, not hyphens in the hardware address. e.g.
sudo arp -s 10.2.2.249 01:00:5e:7f:ff:fa

but I don't see how that enables you to discover its real IP address, on either linux or windows.

---

### Post by efflandt on 2012-06-13
> **The Cog said:**
> arp -s works on linux. 
You need admin rights, so use sudo.
Use colons, not hyphens in the hardware address. e.g.
sudo arp -s 10.2.2.249 01:00:5e:7f:ff:fa

but I don't see how that enables you to discover its real IP address, on either linux or windows.

Once you set a fake IP in your arp cache you can connect to that device using the fake IP and find out from the device itself what its IP is.  I did that to access a print server when I did not know its IP nor how to have it print out its configuration.  Once I connected to it I discovered that someone had accidentally manually set it to a 192.186... IP instead of 192.168... (after correcting its IP it worked).  It was an old used print server that our MIS dept thought was broken.

Also comes in handy for accessing WAPs and wireless bridges when you forget what IP address you set them to.

---

### Post by The Cog on 2012-06-14
> Once you set a fake IP in your arp cache you can connect to that device using the fake IP and find out from the device itself what its IP is
How does that work? 
Without knowing the right IP address, how do you get it to talk to you?

The best I could find was to run:
> sudo tcpdump -n -e icmp
in one window, and then
> sudo ping -b -c 1 255.255.255.255
in another window.

Edit:
It turns out that not many devices will answer a broadcast ping. Some, but not many.

---

