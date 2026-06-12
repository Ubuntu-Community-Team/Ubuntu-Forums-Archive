---
title: "can access ubuntu server"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by jeffrey2009 on 2010-02-10
I just installed unbuntu server on a box and cant seem to access it.  I am new to this.  Any thoughts.  When I try to access the machine via putty i get conneciton timed out.  i bing the server name and it seems to go to external dns.  Do I have to use the ip address of the server.  I did not set up fixed ip address for the server is that required?

---

### Post by abhishek.malhotra35 on 2010-02-10
Try below link:
[http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/](http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/)

Also since its a server, you need to give it a static ip.

---

### Post by Iowan on 2010-02-10
A static address makes the server easier for clients to find - although you can (probably) set up the DHCP server to issue a static lease (based on MAC address). Can you ping it by address? I presume you're using PuTTY to access via SSH. Does the server have SSH server package installed?

---

### Post by jeffrey2009 on 2010-03-02
yes I am able to connecty now, i had to make ip static.  I am using putty and had putty on the server.  Thanks for everything.

---

### Post by Iowan on 2010-03-03
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

