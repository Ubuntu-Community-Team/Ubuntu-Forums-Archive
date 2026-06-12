---
title: "VPN Client and samba/SSH Server on one physical machine."
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by TakeshiKovacs on 2010-06-03
This is really driving me nuts. It's quite unusual that I can't solve a linux problem myself by using google, but with this I'm either too stupid or..... I just don't know. Anyway, let's get to it.

I'd like to access a samba/SSH server which itself is connected to a VPN Server, therefore acting as a VPN Client. As soon as the VPN Connection is established, samba and ssh connections to this VPN Client get a timeout. But not all of them.

To get a better understanding I made an overview. The first one is a general network overview, without any VPN Connection, the second one with the VPN Connection established.

[Network Overview without VPN]("http://i.imgur.com/6YJi0.png")
I can access the server in several ways: 
*From the router via ssh (router runs ipcop with busybox)
*From the laptop via ssh (putty via Windows 7)
*From the laptop via samba
*From the internet via ssh (port forwarding to the ssh server)

Everything is working as it should.

Now the server that runs ssh and samba service connects to a VPN Server on the Internet, this is also working fine. Now it gets weird. The only samba/SSH connection that is still working is ssh directly from the router to the server. Everything else gets a timeout:
*From the laptop via ssh (putty via Windows 7)
*From the laptop via samba
*From the internet via ssh (port forwarding to the ssh server)
[Network Overview with VPN active]("http://i.imgur.com/40eQW.png") 


Why is that? It seems from the little understanding I have of vpn and networking, that incoming packages (like samba request from the laptop) don't get send directly back over eth0 but over the vpn connection. This seems somewhat logic, BUT ssh from the router is still working. Why from the router and not from the laptop? I really can't get my head around it. I've uploaded the relevant part of my configuration to pastebin, hopefully this is all you guys need to point me in the right direction. If you need additional information, please let me know.

[Configuration Overview]("http://pastebin.com/8W0hdm4E")


**tldr;** One Client acts as VPN Client and samba/SSH Server. As soon as the VPN Connection is established samba/SSH stop working, but only partially.

---

### Post by Eldis on 2010-10-11
I'm basically on the same boat as you except my router doesn't do ssh which would be one solution for me.

My setup is very similiar to yours.

What i've been trying to do is:
[http://www.linuxhorizon.ro/iproute2.html](http://www.linuxhorizon.ro/iproute2.html) (example 2)

if that works for you or you solve your problem in some other way please reply to this thread.

---

