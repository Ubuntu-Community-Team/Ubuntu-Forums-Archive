---
title: "getting ready to set up wired network"
date: 2006-02-07
forum: Networking &amp; Wireless
---

### Post by djheadley on 2006-02-07
The 2 comps I want to connect are:

1) 433Mhz Celeron Mendicino, 256mb Ram,card is SMC 8416BTA, with coax, RJ & 15 pin connectoers
2) HP N3330 laptop, 500Mhz, 256mb Ram, PC card is 3C589D-combo, 10baseT, with coax & RJ connectors
3) router is Linksys EFAH05W V3.0 5 port, with RJ connectors

I already am dual booting Ubuntu & WinME on both with the desktop having Ubuntu, Kubuntu and WinME.

Question is, how much troule am I going to have?  What other programs do I need and where do I find them if they're not in the repos?  I don't want to start until I have a good idea what I'm up against.  The last network I unstalled was way back when DOS was the only OS and Novell was the only network software worth talking about.

---

### Post by dickohead on 2006-02-07
There's this really REALLY good technologoy that developed during the times of the Novell rule, it's called TCP/IP, I know silly name, but it's functionality is beautiful. There's this little utility I like to use sometimes called PING, a bit like tennis really!

Anyway.. piss taking aside.

As long as you have this:

10/100mbps Network Cards
Cat5/Cat6 Ethernet cables to each machine
Central hub/switch connecting all the machines (your linksys is this)

You will be able to network quite effectively!

You can take two main approaches to getting them "communicating".
The first is with Static IP addresses. Assign each machine an address similar to: 192.168.1.100, with a subnet mask like 255.255.255.0 and a gateway address that is the same as your router (usually 192.168.1.1 or 10.0.0.1), you can now use ping to determine if the machines can talk to other.

You could also use DHCP, should be built-in to the Router, login to the router via telnet/ssh or web interface to configure it. DHCP assigns addresses automatically, it's fantastic!

As for the operating systems on your machines, the only issues i see is that when sharing files between Linux/Windows you will need to setup a samba on each Linux machine.

As for software, that all depends on how complicated/simple you want things. If the machines don't need to talk then TCP/IP is enough (included by default), but if they need to share files, then you will need Samba to share between Linux-Linux and Linux-Windows.

Good luck!

---

### Post by mdawes on 2008-02-08
Deleted message

---

