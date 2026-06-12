---
title: "Can't find IP. IPChicken shows router IP."
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by Manaan on 2010-05-17
Okay, I'm trying to ssh into an VirtualBox virtual machine and to do that I need to find both my IP and the VM's ip. IPChicken.com gives me my router's IP, and ifconfig gives me an IP on my machine that begins with 192.168.0 which I think means it only works on the LAN. Ifconfig on the VM gives me an address that is different everytime but is usually something like 10.0.x.15 . No idea what to do now. I don't see where the VM's ip came from, or what it is. I doubt my ip would always be 10.0.x.15 on the VM.

I have a feeling that this question will be a piece of cake for a networking guru, but at the moment I'm pretty darned confused.

---

### Post by anomie on 2010-05-17
[ caveat: I've dabbled in Virtualbox a bit, but I am not super familiar with it. ]

IIRC, Virtualbox gives you the option to 1) have your host system provide NAT for the virtualized system; or 2) create a layer 2 bridge between your host system's NIC and your virtualized system's NIC. 

Where are you trying to ssh to the virtualized system *from*? If it's simply from the host system, the latter option should work. If it's from another box on your 192.168.0/24 subnet, I would imagine your host system will need to provide NAT and PAT to your virtualized system. (i.e. Requests to 192.168.0.50:2222 -> 10.0.0.15:22.) If it's from somewhere out on the 'net, your home "router" (NAT device) will need to provide NAT/PAT to the host system, which will need to then provide NAT/PAT to the virtualized system. Ugh. 

Some generalities in my post, but hopefully you get the idea. 

Finally, as a relevant aside,  you might do some quick reading on [RFC 1918 networks](http://en.wikipedia.org/wiki/Private_network).

---

### Post by Manaan on 2010-05-17
Wow, I'm starting to think this ssh attempt is way over my head. I probably should have mentioned this in my first post, but I have almost no networking experience at all. The most complicated thing I've done networking-wise is configure my router by browsing to 192.168.0.1.

The reason I was trying to ssh to the virtual machine was simply to see if I could (it was from the host machine by the way), so I suppose I could remove that from my original post and focus on finding my own IP. I know that on my local network it is 192.168.0.101, but I want to find the non-LAN IP. I don't have a reason for wanting to know the non-LAN IP either, though. I just want to because I don't already know, if you can understand that. Maybe I'll do some more studying of networking later so I can figure out the VM ssh thing by myself.

---

### Post by pirateghost on 2010-05-17
your router's IP is your non-LAN ip.  you are natted behind your router which means that everything BEHIND your router is in the 192.168.0.0 subnet... probably a /24 mask

your virtualbox config is going to confuse you if you dont configure your VM to use BRIDGED networking rather than NAT.  essentially to your VM, your host machine has become the router by using NAT.

---

### Post by Manaan on 2010-05-18
Thanks, that explains everything. I was even able to ssh into my vm!

---

