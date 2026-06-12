---
title: "Linux-native router??"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by balteo on 2009-11-15
Hello,
I have a couple of computers at home, all of which see each other through a router which seems to run MS Windows inside. It appears I have to use smb in order for them to see each other. Is this a problem one of you has encountered before? Is it possible to set up native linux on a router or do I have to purchase another linux-native router?
Thanks in advance,
Julien.

---

### Post by Iowan on 2009-11-15
The router *shouldn't* care what OS the clients run. To "see" (share with) Windows machines will involve Samba, but that's not the router's concern.

---

### Post by DGortze380 on 2009-11-15
I guarantee that your router is not running Windows of any kind.

You need Samba to share with Windows Computers, has nothing to do with your router.

---

### Post by balteo on 2009-11-16
thank you to both of you!

DGortze380: what you say is interesting and puzzling at the same time.
The reason I presumed that my router was running some sort of embedded Windows is that the **ONLY** way I can see a computer from another using nautilus is using this sort of uri: **"smb://alpha/"** (note the **smb** prefix). Hence my assumption.
Do you see what I mean?
Julien.

---

### Post by void09 on 2009-11-16
OK... have you ever heard of 'ping' or 'traceroute'?

- Actually... if the computers are on the same switch/hub, as often is in home networks, then the 'arp' command will show the other computers ethernet address (MAC address)(and no, it's not an Apple -thing this time). ARP=address resolution protocol. This way you can check that the computers are aware of each other on ethernet level.

- One level up: the Internet Protocol. For routing traffic between different ethernet networks (hop by hop from one network to the next and finally to target network/host). Here IP addresses come to play. Use 'ping IP' to verify connectivity (unless firewalls block ping) and use 'traceroute IP' to check what devices are visible on the route to the target.

Routers work on IP level.

On IP we can then run TCP or UDP to carry some payload.

Disk shares are made with SMB/CIFS protocol on top of IP + TCP/UDP. So routers work on a lower level.

---

### Post by jward3010 on 2009-11-16
> **balteo said:**
> ...through a router which seems to run MS Windows inside.
The interesting thing is that NO router runs Windows, they don't make an OS thats compatible. And in fact most would run Linux or UNIX variants. But of course this has nothing to do with your problem as network technology is based on universally accepted standards that transport even SAMBA protocols between all types of different OS's. It's one of the best cases in the world to show how standards are the greatest thing ever.

---

### Post by jward3010 on 2009-11-16
> **balteo said:**
> The reason I presumed that my router was running some sort of embedded Windows is that the **ONLY** way I can see a computer from another using nautilus is using this sort of uri: **"smb://alpha/"** (note the **smb** prefix). Hence my assumption.
This still has nothing to do with the router, in fact this action you're performing doesn't even talk to the router, it's all handled by the two computers in communication with each other. They might just about use the routers switch but thats not the routing capability, thats just simple packet transfer.

---

### Post by DGortze380 on 2009-11-16
I understand it may be confusing if you don't know about networking, but again ... I guarantee that your router is not running Windows. If you're trying to connect to a Windows Computer, you must use smb. If you have another Linux machines on the network, or an Apple, you could enable ssh and connect that way.

All of this still has nothing to do with your router. It's at Layer 2 because all the machines are on the same subnet. Packets (actually frames at this points) are handled by your switch. (And yes, you do have a switch. It's likely built into what you're calling your router).

This may help.

---

### Post by balteo on 2009-11-16
Thanks for your replies 
J.

---

### Post by Iowan on 2009-11-16
Have you gained on your problem? (Sometimes it's like trying to get a drink out of a firehose - too much information coming too fast.)
If not, what will help clear the fog?

---

### Post by jward3010 on 2009-11-17
> **balteo said:**
> Hello,
I have a couple of computers at home, all of which see each other through a router which seems to run MS Windows inside. It appears I have to use smb in order for them to see each other. Is this a problem one of you has encountered before? Is it possible to set up native linux on a router or do I have to purchase another linux-native router?
Thanks in advance,
Julien.
What exactly do you want to achieve? I'm assuming you want to transfer files, and one of the ways you can do it is with SMB even through Linux machines.

Do you want to transfer files another way or are you trying to find a method that is also compatible with Linux, because SMB IS compatible with Linux.

I recommend opening your home folder (in Ubuntu), hitting Ctrl + L to activate the location bar and entering "smb://windows-computer-name", then hit enter.

See how you get on.

---

### Post by balteo on 2009-11-17
Iowan,
The ping command returns:[INDENT]*ping: unknown host beta*
[/INDENT]whereas I see beta in the address bar of Nautilus:[INDENT]*smb://beta/*
[/INDENT]Help me "clear the fog"!
Julien.

P.S. ping 192.168.1.212 works ok...

---

### Post by balteo on 2009-11-17
jward3010,

> What exactly do you want to achieve?

Good question. I am trying to understand why I have to use samba to connect two linux machines. If you tell me there are no other way to transfer files than using samba, no problems. As you said it works well. Just trying to understand what's going on inside...

See previous post about ping beta not working..

J.

---

### Post by Iowan on 2009-11-17
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To for Windows share problems - though it looks like yours might be the other way around. If you can ping by address, but not name, then DNS is not working right. 
 Winbind might help with SMB problems, but not with **ping**. A few options: You can enter name/address pairs in the */etc/hosts* file... but this gets cumbersome, and doesn't work well/long for DHCP networks. 
Another option would be to install a DNS server on your network. Some routers have it built in (some use **dnsmasq**). I use **dnsmasq** for my DHCP/DNS server - it can tie the two (DHCP and DNS) together so I can ping DHCP client machines by name.

---

