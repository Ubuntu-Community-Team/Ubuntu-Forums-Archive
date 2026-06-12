---
title: "Accessing an Apache virtual host from a LAN machine?"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by Parapan on 2011-03-21
Hello all, I am trying to accomplish the following. I'm not able to progress forward because my knowledge of DNS is very limited. I have tried numerous tutorials on google, but my understanding of BIND9 and DNS is still very weak, so I hope someone can clear this up for me :), thanks

Objective : **To allow virtual hosts configured on this Ubuntu machine to be accessible in the LAN by their vhost name as defined in apache. (And not just by LAN I.P).  If I added a vhost called testdomain, on the apache server, I can access it from the apache server by typing [http://testdomain](http://testdomain) in the browser of the server. But I want this to be possible from another LAN machine also..**


So heres the setup :

Router is 192.168.1.1
This Ubuntu machine, i.e the web server is 192.168.1.10 (Static).

All other machines are 192.168.1.x

I can access this web server from any machine on LAN by typing 192.168.1.10 in the browser. No problems.

The problem : [B]I want to be able to access the virtual hosts on the apache server, from a LAN machine by using the Virtual host name and not just the LAN I.P, just like the way I can on the web server . The way I thought about it, there are a few ways of going about this. Please correct me if I am not making sense with the options below. I am trying to get Option2 to work and I would like to know if anyone can suggest ways to go about making it work.
[/B]

Option 1 : Change the /etc/hosts file on every other LAN machine to make the respective Vhost to point to [http://192.168.1.10/vhostDirectory](http://192.168.1.10/vhostDirectory). Effective, but inconvenient because I often have random people bring in laptops once in a while, and having them to edit the hosts file every time is a hassle.


Option 2 : Add a DNS server on the LAN, and somehow (if possible), get the router to redirect requests to the respective vhost on this server if a match is found. This way any device that jumps into the network can access those Vhosts in their browser without any configuration.  Ofcourse the DNS server will require manual updates as and when more Vhosts are edited or added, but this should atleast ensure only 1 master control instead of having the edit hosts files on any random laptop that gets into the network.

Firstly is this even possible? The way I thought about it , I thought I'd add a DNS server to my server machine itself, and then somehow get the router to use this DNS server and check it first before forwarding the DNS request to my ISP. But then I wasn't able to find such an option in my router page (Asus RT N-16), and my attempts at getting BIND9 to work in Ubuntu have been failing because I'm not able to understand exactly the flow of DNS internals. Help is greatly appreciated, or even if anyone has any links or references to posts that deal with this kind of issue would be awesome :D. Thanks a lot everyone.

---

### Post by SeijiSensei on 2011-03-21
> **Parapan said:**
> Firstly is this even possible? The way I thought about it , I thought I'd add a DNS server to my server machine itself, and then somehow get the router to use this DNS server and check it first before forwarding the DNS request to my ISP. But then I wasn't able to find such an option in my router page (Asus RT N-16), and my attempts at getting BIND9 to work in Ubuntu have been failing because I'm not able to understand exactly the flow of DNS internals.

DNS is a complex beast.  Basically you need to add your local domain to named.conf and create a "zone file" for that domain.  Trying to explain all of this in detail is beyond what works well in a forum.  I suggest you start with [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto).  If running DNS seems too difficult, then you'll need to create hosts files on all the client machines.

I'm surprised you can't tell the router which IP addresses to use as the nameserver(s).  If true, you might want to consider disabling the router's DHCP server and running [dhcpd]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server") on your server instead.

---

### Post by Parapan on 2011-03-21
> **SeijiSensei said:**
> DNS is a complex beast.  Basically you need to add your local domain to named.conf and create a "zone file" for that domain.  Trying to explain all of this in detail is beyond what works well in a forum.  I suggest you start with [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto).  If running DNS seems too difficult, then you'll need to create hosts files on all the client machines.

I'm surprised you can't tell the router which IP addresses to use as the nameserver(s).  If true, you might want to consider disabling the router's DHCP server and running [dhcpd]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server") on your server instead.




Yeah, I guess it is. Thanks for the link though, that should be good to get me started on it. Actually I can set DNS servers on my router, but it won't let me define more than two listings, so I have to use those for my ISP's DNS servers.

I guess for now, I'll just try to learn BIND9 from that link and see how it goes, and probably try out the DHCPD, and maybe wait a day or two for replies here :D.. Thanks

---

### Post by SeijiSensei on 2011-03-21
> **Parapan said:**
> Yeah, I guess it is. Thanks for the link though, that should be good to get me started on it. Actually I can set DNS servers on my router, but it won't let me define more than two listings, so I have to use those for my ISP's DNS servers.

No, you don't.  In fact if you end up running your own DNS server, you'll need to replace the first of those servers with the IP address of your own server.  That makes the clients use your server first, then try the ISP's server if yours fails to reply.  I have two internal DNS servers that I've coded into the router.  I never use my provider's servers at all.

---

### Post by Parapan on 2011-03-22
> **SeijiSensei said:**
> No, you don't.  In fact if you end up running your own DNS server, you'll need to replace the first of those servers with the IP address of your own server.  That makes the clients use your server first, then try the ISP's server if yours fails to reply.  I have two internal DNS servers that I've coded into the router.  I never use my provider's servers at all.

Oh yeah your right, now i remember, I was playing around with some files where I came across something like "forwarders { IP1, IP2; }. Makes sense, I should give that a atry , thanks :D

---

### Post by Parapan on 2011-03-22
Ok I removed the DNS entries from my Router and just used my PC's LAN IP instead and it works great :D, Thanks a ton SeijiSensei.

---

