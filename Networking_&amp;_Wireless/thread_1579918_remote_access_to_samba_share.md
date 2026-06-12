---
title: "remote access to samba share"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by tekkenlord on 2010-09-22
Hello all,

I need to access a windows share at my university's server. When I am at the university, I can access the share by nautilus (or dolphin) in a similar way to ftp:

smb://domain%5Cusername@server/share

The thing is that when I try the above anywhere else except the university, it does not connect.

I guess it has something to do with the domain, but I am not sure... any ideas please? Thanks.

---

### Post by e79 on 2010-09-22
I'm not sure I understood but are you trying to reach a Samba Share over the internet without accessing their network with VPN first ?

---

### Post by tekkenlord on 2010-09-22
Well, I am not sure really...I am a newbie when it comes to samba. All I know is that I can access the share _only_ when I am using the computer at uni.

Hmm, so what is the thing with the VPN?

---

### Post by e79 on 2010-09-22
> **tekkenlord said:**
> Well, I am not sure really...I am a newbie when it comes to samba. All I know is that I can access the share _only_ when I am using the computer at uni.
 
Hmm, so what is the thing with the VPN?
 
a VPN is a "Virtual Private Network", a way to connect to a place (IE University) that is encrytpted and secured, allowing you to use the services (Samba in this case) as if you were there.
 
It would be the same thing in Windows; in order to get to a Share on a server at your company or university, you would first need to initiate a VPN connexion to secure your communication with those server (so no one can 'sniff' or hijack you connexion). And we're not speaking about the FTP protocol here (this is another story).
 
You should ask the IT department of your university to see if :
 
1. They have a VPN connexion available for students.
2. They could teach you on how to configure and use it.
 
Once the VPN would be connected you should be able to type something as "smb://domain%5Cusername@server/share" to access your share as if you were sitting at the university (depending on DNS/DHCP configuration but this is another story).
 
(Basicly what is blocking you is the fact that you are trying to access a Local/Internal share at the university from your home (ie) but the firewall is blocking you for obvious reasons, its protecting the local network from outside and non-authorized communications, basics of routing and firewalls :) .
 
read here for more info on VPNs :  [http://en.wikipedia.org/wiki/VPN](http://en.wikipedia.org/wiki/VPN)
 
Hope this helps

---

### Post by tekkenlord on 2010-09-22
You are the best, thank you very much. I will ask the department's IT.

---

### Post by e79 on 2010-09-22
> **tekkenlord said:**
> You are the best, thank you very much. I will ask the department's IT.
 
The pleasure is all mine !

---

