---
title: "Failed to retrieve share list from server"
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by halfhearted on 2012-10-26
I am trying to connect my ubuntu 12.04 PCs to my Micronet SP781W printer server so that I can print using my home wifi network. The printer server was originally set up using Windows and its IP is 192.168.2.110. I cannot reach it using this IP in FireFox and I cannot ping it from a console. If I "Browse Network" from Nautilus then I get to tyhe Windows Network icon. If I click on this it opens to show the Worgroup icon. If I click on this I get the error message "Failed to retrieve share list from server". Is this failure the reason I cannot reach or ping the printer server? What can I do? Any help gratefully received.

---

### Post by lykwydchykyn on 2012-10-26
> **halfhearted said:**
> I am trying to connect my ubuntu 12.04 PCs to my Micronet SP781W printer server so that I can print using my home wifi network. The printer server was originally set up using Windows and its IP is 192.168.2.110. I cannot reach it using this IP in FireFox and I cannot ping it from a console. If I "Browse Network" from Nautilus then I get to tyhe Windows Network icon. If I click on this it opens to show the Worgroup icon. If I click on this I get the error message "Failed to retrieve share list from server". Is this failure the reason I cannot reach or ping the printer server? What can I do? Any help gratefully received.

Ping, web services, and Windows Networking all operate on different network protocols, so the errors are probaly not related.

The first thing I'd do it install "nmap" from the repository and scan the device for open ports, like so:

```

nmap -PN 192.168.2.110

```

If the device is connected to the network, this will tell you which ports are open, and thus which protocols you can try to use to communicate with it. 

Post the output of that command here and we can go from there.

---

### Post by halfhearted on 2012-10-26
I installed nmap and below is the output. What does it mean? Anyone?

user1@user1-901:~$ nmap -PN 192.168.2.110

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-10-26 22:24 BST
Nmap scan report for 192.168.2.110
Host is up (0.87s latency).
All 1000 scanned ports on 192.168.2.110 are filtered

Nmap done: 1 IP address (1 host up) scanned in 65.08 seconds

---

### Post by lykwydchykyn on 2012-10-26
It means most likely that either your print server has a different IP, or it's not working properly.  Does it currently work correctly for other systems on the network?

---

### Post by halfhearted on 2012-10-27
Right, I ran - - -
nmap 192.168.2.0/24
to attempt to see if the Micronet printer server does not have the IP
that I was assuming. Leaving out the IPs I know it reported this - - -

Nmap scan report for 192.168.2.10
Host is up (0.0061s latency).
Not shown: 992 closed ports
PORT     STATE SERVICE
23/tcp   open  telnet
80/tcp   open  http
515/tcp  open  printer
631/tcp  open  ipp
9100/tcp open  jetdirect
9101/tcp open  jetdirect
9110/tcp open  unknown
9111/tcp open  DragonIDSConsole

So, it would appear that the IP is actually 192.168.2.10 and not 192.168.2.110. This is baffling since I thought that I'd set it to 110. Do these port numbers look like they might be for a printer server? Hard to see how I could have got this wrong, I'd written it down. What do the words next to "open" mean? Are these the typical uses for these various ports? Thanks for your help.

---

### Post by lykwydchykyn on 2012-10-28
> **halfhearted said:**
> Right, I ran - - -
nmap 192.168.2.0/24
to attempt to see if the Micronet printer server does not have the IP
that I was assuming. Leaving out the IPs I know it reported this - - -

Nmap scan report for 192.168.2.10
Host is up (0.0061s latency).
Not shown: 992 closed ports
PORT     STATE SERVICE
23/tcp   open  telnet
80/tcp   open  http
515/tcp  open  printer
631/tcp  open  ipp
9100/tcp open  jetdirect
9101/tcp open  jetdirect
9110/tcp open  unknown
9111/tcp open  DragonIDSConsole

So, it would appear that the IP is actually 192.168.2.10 and not 192.168.2.110. This is baffling since I thought that I'd set it to 110. Do these port numbers look like they might be for a printer server? Hard to see how I could have got this wrong, I'd written it down. What do the words next to "open" mean? Are these the typical uses for these various ports? Thanks for your help.

That is definitely a print server; the services listed are the standard uses for those ports (known as "Well known ports").  Direct your browser to that IP and it should give you a web interface.

---

