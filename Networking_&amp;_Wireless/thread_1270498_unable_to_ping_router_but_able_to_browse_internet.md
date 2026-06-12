---
title: "unable to ping router but able to browse internet"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by wired99 on 2009-09-19
I've encountered a very peculiar problem.

I cannot ping anything other than my own computer.

I have a pc with Ubuntu 8.04, a pc with windows Vista, and a HP printer, all three individually connected by ethernet cables to my router which in turn is connected to my internet modem.

I can access the internet with both Ubuntu and Vista, and I can print with both computers as well

I've been unsuccessfully trying to set up my computers as a home network to share files.

I've discovered that I cannot ping anyone - not even my router with my Ubuntu, however I can successfully ping my router, printer, and anyone on the internet with my Vista.

I cannot ping my Ubuntu with Vista. 
I do have access to the internet and am able to print with Ubuntu.

I would like to network my computers to share files. I have read many many guides but I have only achieved more confusion.

this is what I get when trying to ping ANYONE:

me@me-ubuntu:~$ ping -c 3 [www.google.com]("http://www.google.com")
PING [www.l.google.com]("http://www.l.google.com") (209.85.225.104) 56(84) bytes of data.

--- [www.l.google.com]("http://www.l.google.com") ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2011ms

This is what I get when I ping my own address:

me@me-ubuntu:~$ ping -c 3 192.168.1.101
PING 192.168.1.101 (192.168.1.101) 56(84) bytes of data.
64 bytes from 192.168.1.101: icmp_seq=1 ttl=64 time=0.068 ms
64 bytes from 192.168.1.101: icmp_seq=2 ttl=64 time=0.055 ms
64 bytes from 192.168.1.101: icmp_seq=3 ttl=64 time=0.056 ms

--- 192.168.1.101 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.055/0.059/0.068/0.010 ms

Can anyone help me?

---

### Post by wired99 on 2009-09-20
Is there a tool that might help me diagnose the problem? 
(preferably GUI, command line is great unless one doesn't fully understand every command and its consequences)

My goal is to set up my computers to share files, but they cannot see each other

---

### Post by badger_fruit on 2009-09-20
It seems to resolve the DNS ok for google (209.85.225.104)
can you access web-pages OK from your browser (in ubuntu)?

---

### Post by wired99 on 2009-09-20
I can access the web with no problem (with Ubuntu), but there is a 100% loss of packets whenever I ping anyone.
This only happens with Ubuntu.
I'd like to connect my home computers together but Ubuntu can't see them.
I think it might be related to the fact that I can't even ping them.

---

### Post by wired99 on 2009-09-20
is there something I should do in Firestarter?
I've set it to allow connections from the IP address of my other computer but I still can't network the computers together.

---

### Post by wired99 on 2009-09-20
I found a solution to connect my computers in a different thread.
here is a nice tutorial:

[http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

I still get 100% packet loss when pinging but at least I can now share files between my computers.

I would like to understand why 100% loss but everything works ... so I guess I'll continue my search at my leasure

---

### Post by wired99 on 2009-09-26
I disabled ICMP filtering in Firestarter and now I can see results of ping.

In Firestarter: Edit - Preferences - ICMP Filtering

---

