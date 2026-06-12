---
title: "Cannot Access Windows Share Drives"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by rss7 on 2009-02-08
Hello,

My WinXP machine is 192.168.1.101 /24.  The workgroup name is MSHOME.  I have Ubuntu 8.10 on another machine whose IP address is 192.168.1.101 /24.  I can ping winXP machine from Ubuntu machine.  I can print from Ubuntu machine to a shared printer hanging off of winXP machine.  I can browse the shared folders on winXP 192.168.1.101 machine by using smb://192.168.1.101 in Firefox browser on Ubuntu machine.  When I try Places-Metwork. I get "Window's Network" - if I click on it I can see the MSHOME network.  WHen I click on MSHOME I get nothing.  

If I open up a terminal window on Ubuntu machine and do "ping MSHOME"  it successfully pings 67.63.55.3.  I have no idea what this address is.  It might be the address of my ISPs DNS server.  I think I have some sort of name resolution problem.
Any ideas?
Thanks

---

### Post by Iowan on 2009-02-09
The two machines must have different IP addresses - 192.168.1.101 for both won't work.  You can't ping a workgroup name (at least as far as I know).

---

