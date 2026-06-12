---
title: "Ubuntu Server - 9.10 .local not resolving?"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by Zeon100 on 2009-11-08
Hi everyone,
I am just entering the world of linux through Ubuntu Server. In this case we are wanting to offer an SSH server for our clients to drop files off which we can then access internally through SMB shares on our Active Directory network. I am following the Kerboros/Samba guide to get this setup and one of the first steps is to get Ubuntu to resolve the DNS of a domain controller.

I have installed desktop onto the server and used network manager to setup two NICs and set the DNS server as a Windows Server 2008 Domain Controller. This works fine to ping virtually any address however it won't resolve our local domain:
pbs.local

In this case the domain controller is called apollo so if I ping apollo.pbs.local it fails, however I can ping say google.com or indeed resolve ubuntu.com. It seems there is an issue with resolving ".local" FQDN? Tips?

Thanks,

System:
Ubuntu 9.10 server (64bit)

Server hostname:
Atlas

Server FQDN
atlas.pbs.local

---

### Post by Zeon100 on 2009-11-08
I have come across the fix, I've just tested and it works!

[http://longerthan5.blogspot.com/2008/05/help-i-cant-ping-fqdns-in-ubuntu.html](http://longerthan5.blogspot.com/2008/05/help-i-cant-ping-fqdns-in-ubuntu.html)

> 
Okay, for this tip I need to specify that I have only ever encountered the problem on Ubuntu 7.10 (Gutsy Gibbon). However, from what I read while researching the problem it also applies to Ubuntu 8.04 (Hardy Heron). Basically, what happened was I could ping my mail server by its name (rex), but not its Fully Qualified Domain Name (rex.cms.local).

Turns out there is some strange interaction between DNS and Avahi (no not the woolly lemur the Linux implementation of Zeroconf) that only rears its ugly head when your local domain ends in a .local. Now, I hear that Avahi is great if you have a network of computers, no DNS server and no desire to set one up, but I don't have that problem. I have a DNS server dang it!! Two of them to be precise. All I want is nice easy DNS resolution!!

Well here is your solution:

[LIST]
[*]Open **/etc/nsswitch.conf** in your favorite text editor (I like nano, vim works, if you are an emacs user.......well I guess you can keep reading).
[*]find the following line:
**hosts: file mdns4_minimal [NOTFOUND=return] dns mdns4**
[*]Change it to:
**hosts: files dns**
[*]Thats it!!
[/LIST]
Once again, it will break Avahi, but most likely you wont need it. 


---

