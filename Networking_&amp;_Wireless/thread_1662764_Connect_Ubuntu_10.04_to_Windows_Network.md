---
title: "Connect Ubuntu 10.04 to Windows Network"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by mnielsen1984 on 2011-01-08
I have a simple home network that I am trying to connect Ubuntu 10.04 to.  I have no server yet, although I will possibly be adding one in the near future.

I have no problem getting a Internet connection on for Ubuntu. I also can access the Ubuntu machine from my Windows 7 computer.  The problem I'm having is being able to access any computer from Ubuntu.

When I go Places->Network, the only option is 'Windows Network'. Opening this, I get two options, 'MSHOME' and 'WORKGROUP' I attempt to open both, and get the same response: "Unable to mount location, Failed to retrieve share list from server."

How am I able to access the other computers from Ubuntu?

Thanks.

---

### Post by thomasw_lrd on 2011-01-08
The way I did it was to find the ip address oft he windows computer.  And type in my web browser

smb://ip addres/windows share

I believe that Ubuntu comes with samba installed, but you might want to install it if that doesn't work.

---

