---
title: "NFS and DNS"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by Praxicoide on 2010-05-08
Hi.

I'm trying to connect two laptops via a router and wi-fi. One is a Dell with Ubuntu 10.04 Lucid Lynx, and the other is a Vaio with Xubuntu 9.04 Jaunty Jackalope.

Since these are both Linux machines, I tried with NTS. I installed the required packages (nfs-kernel-server, nfs-common and portmap in ubuntu, which would be the "server" and the last two in xubuntu, which would be the "client").

So I set up /home/name/Public as a shared folder successfully (available to the "world" with read/write access, according to exportfs).

But, on the client computer, when I tried to mount the shared folder, I get a DNS error, saying it does not have an address assigned to the hostname.

So I got the IP adress off the server with ifconfig, and used that.

With the IP, I could connect successfully and share files.

The problem is that I'm using DHCP, not a static IP, so I can't use this permanently (I can't put this in /etc/fstab). I would have to get the IP and mount everytime.


So, is there any way to use the DNS hostname to mount the shared folder on start up? How would I do this?

---

