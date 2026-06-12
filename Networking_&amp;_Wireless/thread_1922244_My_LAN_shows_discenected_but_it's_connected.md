---
title: "My LAN shows discenected but it's connected"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by SabbirA1 on 2012-02-08
I'm using Ubontu 11.04.....

I'm a new user of Ubontu Operating system...

I'm using netbook "DOEL Basic model". Problem is i enable the internet. I'm using Boardband. I'm also edit the Mac address, Config IP address manually & save it. But it did n't work. It shows WAN disconected. But in WINDOWS XP my net is running. I can't Understand anything. I want to stay with ubontu. But if my net is not connect then i :( ...... Plez help me vhaia.....
I can't install my NET Driver... 

My IP - MAC Address & Driver details is given below:

IP ADDRESS DETAILS:
===================
Phyical Address : 4C-00-10-51-E4-55
IP Address      : 172.16.0.167
Subnet Mask     : 255.255.255.0
Default Gateway : 172.16.0.254
DNS Servers     : 223.27.112.253
                  8.8.8.8



MY DRIVER DETAILS: (jme-1.0.5.tbz2)
===================================
Linux Driver for the JMicron(R) JMC250/JMC260 PCI-E Ethernet Adapter


Contents

- Readme First
- Building and Installation
- Command Line Parameters
- Known Issues

Readme first

This file describes the Linux Driver for the JMicron(R) JMC250/JMC260 PCI-E Ethernet 
Adapter. Version 1.0.5 supports the 2.6.16 or above kernels.

Install Requirement:
1. Kernel srource HEAD
2. Compiler

Building and Installation

Install Process:
1. Decompress jme-1.0.5.tbz2
   #tar xjvf jme-1.0.5.tbz2

2. Change directory to jme-1.0.5

3. Compile driver with root permission
   # make install
   The binary will be installed as:
   /lib/modules/<KERNEL VERSION>/kernel/drivers/net/jme.ko
4. Load the driver:
   # modprobe jme
Command Line Parameters

1. Assign an IP address, where x is the interface number:
   # ifconfig ethx <IP_address>
Known Issues

None





Plez Help me out........ :(

---

### Post by jonobr on 2012-02-08
Open a terminal window in your ubuntu box and post the results of 
```
cat /etc/network/interfaces
cat /etc/nsswitch.conf
cat /etc/resolv.conf
```

also post the results of an ifconfig would help

Lastly 
```
lshw -C network
```

---

### Post by Iowan on 2012-02-08
In previous versions, if you configured an interface in */etc/network/interfaces*, Network Manager wouldn't touch it - and claim it disconnected (similar to what you're seeing). Network Manager has gotten more aggressive in recent versions -so that might not be true any more.

---

