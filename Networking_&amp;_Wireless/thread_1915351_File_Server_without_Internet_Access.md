---
title: "File Server without Internet Access"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by MOGuy78 on 2012-01-26
I'm wanting to set up a file server for my home network.  I would like all of my home pc's to have access to the server, but I don't want the server itself to be connected to the internet.

In many of the threads that I've read, it says that if your setting up a static ip, your /etc/network/interfaces file should look something like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1


For my purpose, would I need all of this?  If not, what would I need?  As I said before, I don't want the server to be connected to the internet.

---

