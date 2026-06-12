---
title: "Redirect DNS.. dhcp server etc.."
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by cmolson on 2009-01-09
Okay I wasn't exactly sure what to put in the title. 

**Firstly:**
I have purchased a domain from noip.com
I have the noip client updater setup and working(since I have a dynamic IP at home)

**Current Setup:**
I have a linksys WRT600N router connected to cable internet. Currently it is providing IPv4 addresses to computers(192.168.1.0/24)

I have a 'server' PC setup with Ubuntu Server 8.10 x64.
It has VMware server installed and has several virtual machines.
All of the virtual machines are setup to use Bridged networking so they all have their own addresses on the network.

Everything is working, I can access the virtual machines various services (FTP, web server, ssh etc) by using their respective local ip.


**What I would like to do:**
Since I bought a domain name lets say foo.com, I would like to setup each virtual machine to be computer1.foo.com and computer2.foo.com etc. This way I can access them all from school/workw/anywhere.

I have played around with using the linksys routers port forwarding tool, but since I have several services (ssh) all running on the same port I can only access one at a time. I could change the port on each machine but then it becomes hard to manage them since I have to remember what machine is setup on what port.

What I want to be able to do is access each computer from outside my LAN by using a hostname like computer1.foo.com, computer2.foo.com etc.

I have setup a dhcp server before, but I have only gone as far as assigning certain ip's to specific MAC address (reserved static ips).

What I am looking for is the term for what I want to do (so  I can research it more), or even some guides or something online. I just need to be pointed in the right direction.

Thanks!

---

