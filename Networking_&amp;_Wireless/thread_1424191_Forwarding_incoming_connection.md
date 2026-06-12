---
title: "Forwarding incoming connection"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by ArpSoft on 2010-03-07
I have 2 pc's at home. One is running Windows 7 x64 and other one is  running on Ubuntu Linux Server 8.04

My PC that is running on Windows 7 is connected to internet directly and  connection is shared for Ubuntu server, which means that i can browse  the net from ubuntu machine also... Anyway, since my Ubuntu is a server,  i would like to make it accessible from global net, but there is a  problem... 

When user enters my ip it connects him on my server which i  have installed on Windows7... 

So, is there any way that i can make my  Windows 7 machine to redirect user on 192.168.137.2 (Which is the IP of  linux server pc) ?

---

### Post by bernied on 2010-03-07
> **ArpSoft said:**
> I have 2 pc's at home. One is running Windows 7 x64 and other one is  running on Ubuntu Linux Server 8.04

My PC that is running on Windows 7 is connected to internet directly and  connection is shared for Ubuntu server, which means that i can browse  the net from ubuntu machine also... Anyway, since my Ubuntu is a server,  i would like to make it accessible from global net, but there is a  problem... 

When user enters my ip it connects him on my server which i  have installed on Windows7... 

So, is there any way that i can make my  Windows 7 machine to redirect user on 192.168.137.2 (Which is the IP of  linux server pc) ?
Sorry I don't have an answer, except that this is really a Windows question. You'll need to set up the Windows box to forward ports to the Linux box.

A quick google found [these instructions](http://articles.techrepublic.com.com/5100-10878_11-1056226.html) for WinXP. I've not used W7, so don't know what is different.

A cheap modem/router could solve the problem, then you would not need the Windows box running to access the net from the Linux box either.

---

### Post by ArpSoft on 2010-03-07
That article isn't helping :( Since it is written for XP, and on win 7 there is a totaly different interface for managing network services... Ive posted the same thread on 4-5 windows 7 forums and it seams that nobody has an answer to my question :( anyway, i forgot to mention that i use a Wireles 802.11**a **connection, so, no router, modem etc. only a crossower cable conected to anthena... 

And also, when I start a WAMP server on Win7, it is working really good, i can access it from anywhere...

It's just that simple little thing that is killing me...

---

### Post by Charly85551 on 2010-03-08
To me it looks like you are using the Win7 machine as a bridge for your Ubuntu-server.
(I have done this before but to make it work properly you need special software for it.)
Your life would be a lot easier if you invest in a small router set between your current internet access and both PC's. There are small and cheap boxes available like the EDIMAX BR-6214K. All you need to do is to activate port forwarding in this router for one or both of your PC's and then they are reachable from internet. (in the EDIMAX-box this function is called virtual server!). If you want to go this way I can give you more details of how to set-up the IP-network for it.
cheers
Charly85551

---

