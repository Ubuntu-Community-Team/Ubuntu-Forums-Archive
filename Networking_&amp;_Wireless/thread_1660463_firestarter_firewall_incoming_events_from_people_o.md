---
title: "firestarter firewall incoming events from people on my network. i think?"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by topbayder on 2011-01-05
i sometimes use a shared work wifi, secured with a password so only a handful of others can use it. and i keep getting events popping up from ip's that i think are from others on my network. not all the time or constantly but i just want to know how i can find out more.

the ip's i have had come up are: 
192.168.0.22 
192.168.0.23 
192.168.0.26

i opened SYSTEM>ADMINISTRATION>NETWROKING TOOLS and used the "lookup" tab but i dont really know what the output means. is there other techniques for bringing up something like a computer name. to see if it is someone on the network and try to find out who, if anyone actually is, trying to hack my computer?

Thanks

---

### Post by PatchesTheCaveman on 2011-01-05
If your wireless router has a DNS server that resolves local IP addresses, this command will lookup the hostname of the computer:
```
host 192.168.0.22
```
Open the Terminal in Applications > Accessories to run that command.

You can also find that information from the "DHCP Clients" list in the router configuration, if you have access to that.

That being said, there are any number of reasons you could be getting hits on your computer from other IP addresses at work.  The most likely cause is that someone is using the "Network Neighborhood" function of Windows to look at all the computers on the network that might have file shares available.

---

### Post by topbayder on 2011-01-07
i tried what you recomened and got this:

:~$ host 192.168.0.32
Host 32.0.168.192.in-addr.arpa. not found: 3(NXDOMAIN)

did it just after i got a hit on my firewall events list.

i dont have access to the router btw.

---

### Post by mikewhatever on 2011-01-07
Don't mean to sound too ominous, but this kind of partisan activity on your work's network can actually get you fired. If you really think someone tried hacking your computer, talk to the sysadmin in charge. If not, that is, you simply try doing some private hacking of your own, find another place to learn.

---

### Post by endotherm on 2011-01-07
+1 to Mike. no point in getting fired over it.

if you do have proper authorization, look into ZenMap, a network infomation gathering tool. 

keep in mind, these other addresses are probably not trying to attack you. samba/netbios broadcasts information and attemtps to learn about other computers on the network by default, so they are probably just trying to see if you are part of their workgroup, and back off when you don't respond. this is all automated, not somthing that their operators know is happening.

---

