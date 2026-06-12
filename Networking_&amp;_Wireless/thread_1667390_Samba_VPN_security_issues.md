---
title: "Samba VPN security issues"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by ale_login on 2011-01-14
I'm kind of confused and hope someone will help:

I'm running a Ubuntu 10.04 server and I enabled VPN using pptpd.
In particular, I added to /etc/pptpd.conf the following lines:
localip 192.168.1.100 (server address)
remoteip 192.168.1.200

My understanding of VPN is that when I connect to the server, it sees the client with the remoteip address that I chose (am I wrong?)

Now I wanted to set up Samba in such a way that only if I'm connected to the VPN I can log in. I though to achieve this adding to /etc/samba/etc.conf:
hosts allow 192.168.1.200 (same as remoteip before)

But that doesn't work. Logging in from a windows machine, it doesn't matter that I'm connected to the VPN or not, I can ONLY access samba if hosts allow is set on the client's original ip.

...?

ps. i don't know if it can help, but windows is definitely not split tunneling. or at least, it goes out on the internet with the server's ip address when i log into the VPN.

---

