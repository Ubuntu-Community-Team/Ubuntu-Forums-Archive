---
title: "Setting up an intranet in Ubuntu 10.04"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by stunet on 2010-07-07
Hi,

hope this topic goes here, but what I want to do is make an old computer of mine that I use for web development be accessible to anyone within my LAN only.

so in a nutshell i don't want the world wide web to be able to access this server since I use it for development work only and i do most of my actual development work on another system since most of the applications i use requires windows.

I know you can block incoming traffic to all IPs or add individual IPs to allow in, but how can i make the firewall only accept incoming traffic from those within my LAN network?

if you wish to know what I'm using to configure my firewall, I'm using firestarter on this server(willing to use a different firewall manager if someone recommends a different one).

I really appreciate this, if I get this working correctly, it'll save me the hassle of swapping files via flash drive :)

---

### Post by alphacrucis2 on 2010-07-07
> **stunet said:**
> Hi,

hope this topic goes here, but what I want to do is make an old computer of mine that I use for web development be accessible to anyone within my LAN only.

so in a nutshell i don't want the world wide web to be able to access this server since I use it for development work only and i do most of my actual development work on another system since most of the applications i use requires windows.

I know you can block incoming traffic to all IPs or add individual IPs to allow in, but how can i make the firewall only accept incoming traffic from those within my LAN network?

if you wish to know what I'm using to configure my firewall, I'm using firestarter on this server(willing to use a different firewall manager if someone recommends a different one).

I really appreciate this, if I get this working correctly, it'll save me the hassle of swapping files via flash drive :)

You don't need to do anything special. The general public won't be able to access it at all unless you have specifically configured port forwarding on your internet router.

---

### Post by stunet on 2010-07-07
ok cool, wasn't 100% sure.

thanks for the help :)

---

### Post by alphacrucis2 on 2010-07-07
> **stunet said:**
> ok cool, wasn't 100% sure.

thanks for the help :)

The question we usually get is the other way around, where someone has set up a web server at home and they want it to be accessible to the general public. The problem being that the home web server has a private RFC type ip address like 192.168.x.x or 10.x.x.x, which aren't routable over the internet. What has to happen is for the general public to connect to your router's public ip address on port 80 and/or 443 and the router is set up to port forward to the real internal private ip address of the web server. The public can even connect using a name rather than an address, if you set it up using something like the [dyndns]("http://www.dyndns.com/") service.

The caveat being that with some ISP's, this violates their terms of service, as some of them don't like home customers running web servers over their home broadband connections.

---

### Post by stunet on 2010-07-07
I do have one more question, this regarding ftp

going by the same question can i make ftp work internally? dont have much ftp expereince(as in setting it up, know how to use it) if not, any suggestions on uploading files to the web server?

---

### Post by stunet on 2010-07-07
nevermind, figured it out myself :D

thanks for all the help.

---

