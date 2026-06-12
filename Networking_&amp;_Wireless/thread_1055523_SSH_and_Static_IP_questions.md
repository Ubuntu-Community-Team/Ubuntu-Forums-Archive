---
title: "SSH and Static IP questions"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by thenocturnalhoodie on 2009-01-30
Hello everyone
So I am attempting to run an SSH server on my machine. I've got the software installed, and it's working.
I tried logging into my computer from my laptop on the same network, but I don't know my IP address. I know that it's not static yet, and I want to make it. However, I'm worried. I read the tutorial on doing it, and I am still confused/cautious. 

Does it matter at all waht I choose as my IP address? Do i have to stick to any regulations? That's my biggest concern, I believe.

Also, I tried to figure out the Public Key Authentication thing, but I really am lost. How specifically do I make this more secure?

---

### Post by finku on 2009-01-30
Do you have a DHCP running on your network? did you try 'ifconfig'?

---

### Post by Iowan on 2009-01-31
Your static IP address will need to be in the same subnet as your other machines.  If you have a DHCP server, your static address must be outside the range the server uses. (You should also avoid the server's address).  If you use the "standard" 255.255.255.0 (/24) netmask, you should also avoid the network address (X.X.X.0) and broadcast address (X.X.X.255). 

Another option is to set up your DHCP server to issue a "static lease" (based on MAC address) to your machine.  It'll always get the same IP Address, but you don't need to set up a static address in the machine. (More work on the DHCP server, but you won't need to fight with Network Manager.)

---

### Post by thenocturnalhoodie on 2009-01-31
> **Iowan said:**
> Your static IP address will need to be in the same subnet as your other machines.  If you have a DHCP server, your static address must be outside the range the server uses. (You should also avoid the server's address).  If you use the "standard" 255.255.255.0 (/24) netmask, you should also avoid the network address (X.X.X.0) and broadcast address (X.X.X.255). 

Another option is to set up your DHCP server to issue a "static lease" (based on MAC address) to your machine.  It'll always get the same IP Address, but you don't need to set up a static address in the machine. (More work on the DHCP server, but you won't need to fight with Network Manager.)

I like the second option, because last time I tried setting up a static IP, it really messed up my system. I did something wrong, and it was very difficult to recover, so I'd prefer to have it a little more secure for me.

---

