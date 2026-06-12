---
title: "SSH - RLOGIN Help please!"
date: 2006-02-20
forum: Networking &amp; Wireless
---

### Post by USA1 on 2006-02-20
Hello,

I am trying to get SSH, telnet and rlogin working on my systems.

I have two computers, laptop running FC4 and this desktop running ubuntu 5.10.
They are both hard wired to a belkin wireless router.
They both connect to the internet and they can ping each other.
I can only ping each computer using IP, but it wont connect using hostnames, why?

I am trying to get these utilities to work on these two machines but it is not happening.  It tells me that it can not connect and that it can recognize the hostname I am trying to connect to.

First, how do I get DNS to work on these to machines so that I can reference them by host name?

Second, how can I check for SSH package installed?
How can I install the Rlogin and SSH, telnet using ubuntu?

Last but not least,
I have a third labtop running ubuntu that I am trying to connect via wireless.
If I disable the WEP feature on the router, ubuntu will connect no problem.
If I enable the WEP feature, provide the key to ubuntu, but it will not connect.
what am I doing wrong, how can I get this to work?

Also, the desktop computer is an old NEC GT200 machine running on AMD K6-2 3dnow, 500mhz. When this computer was new, it was the fastest thing on earth. Now I can hardly type this post because it is acting so slow.

I upgraded the ram from 96mb to 512mb max, but that doesn't help, it really drags....  it takes for ever to open a window in ubuntu gui.

Something must be wrong with this computer being so slow...

---

### Post by AndyCooll on 2006-02-20
The first couple of points, your hostname issue. You'll probably need to edit your hosts file on each box.

```
sudo vi /etc/hosts
#Then add a line for each computer on your network in the following format:
IP_address  name_of_computer
```

At the moment you are typing in a name and the box doesn't know what IP address to translate this to.

Secondly, have you actually installed SSH? It doesn't come installed by default. If not you need to install OpenSSH client and server using Synaptic.

For your wireless and wep issue, can you please post a copy of your /etc/network/interfaces

:cool:

---

