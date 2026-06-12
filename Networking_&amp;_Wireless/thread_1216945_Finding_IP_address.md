---
title: "Finding IP address"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by tonymoloney on 2009-07-18
I have inherited an unusual network. Because of topological constraints, the network has a direct ADSL line which then goes to a WAP and antenna which distributes the signal to users on the network. Each user has their own antenna and WAP to receive the signal.
The original network designer decided to give each user WAP a static IP but due to carelessness or poor documentation, not all of these IPs were recorded.
I now have to reconfigure some of these WAPs, but as I don't have the IP for them. I'm finding it very difficult. I can physically reset them to factory default, but this involves crawling up into the ceiling space to find the actual WAP.
Does anyone know of some terminal command that will let me query the IP of the WAP. I tried traceroute, but that did not give me any information before the gateway, which I already knew.
BTW, I'm 70yrs old, living in a retirement village, so you can understand why I don't want to do the physical reset unless I'm absolutely forced to.

---

### Post by Riaku on 2009-07-18
[http://ubuntuforums.org/showthread.php?t=235538](http://ubuntuforums.org/showthread.php?t=235538)

---

### Post by lensman3 on 2009-07-18
Try nmap with 192.168.0.0/16 set to the local network IP number.  This will scan all IP numbers on your network and return what the other end host machines are.

nmap -v -sP 192.168.0.0/16

Take a look at the -T4 option.
nmap -v -A -T4 192.168.x.x/24

Hope this helps.  Remember this is a hacking tool and using it without permission could get you in a lot of trouble.

---

### Post by tonymoloney on 2009-07-19
Thanks for the help. So far nothing gets me what I want. I'm also following up instructions on wireshark from a private post.

Maybe I should try to describe our network better:

Starting from any of the homes in the network we have the home computer connected to the home WAP via RJ45 cable (This makes the home computer think that it is on a wired network)
The home WAP talks to the club WAP via wireless.
The club WAP is connected to an Annexe M modem via RJ45 cable.
This modem is connected to our ISP via a dedicated "naked" ADSL+ line.

I know the IP of the club WAP. It is the IP of some of the home WAPs that I am trying to determine

Thanks
Tony

---

