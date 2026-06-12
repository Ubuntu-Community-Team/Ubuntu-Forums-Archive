---
title: "My love to all open sourcers"
date: 2009-08-21
forum: Multimedia Software
---

### Post by OpenSourceForAll on 2009-08-21
Hello all linux users and open sourcers, only last year have I discovered all of what you do, I have downloaded clamwin, and audacity and am excited for more open source programs, I am only computer savy I am not a programmer but I was wondering if any of you could help me with t his dilemma, I am doing research for a buisiness. Intellectual property needs to be very safe and secure, I dont know much about how a firewall works, but this is what I want to know, the connections between the computers where they go , like I thought it was called a port? but apparently its a tunnel? and I want to know if there is a program for a video chat interface that would open up behind the tunnel and if encypting the signal would help at all, my goal is to find a program that keeps the video conference extremely secure and how the connections between the computers work

thank you for your help

---

### Post by jdackle on 2009-08-22
Hi OpenSourceForAll,

I'm also no developer, just a savy user like yourself, but discovered opensource some eight or nine years ago. Very glad I did indeed! ;)

Anyways, your question should probably be broken down to pieces and, as far as I can infer of what you said so far, its bulk should probably fit better in the "Networking & Wireless" or even more in the the "Security Discussions" of this forum.

So, trying to break down your question(s):

1. The solution you are looking for is to be implemented in a Linux or a Windows envirionment?
(This may sound like a silly question but you did refer ClamWIN (Windows version of the original ClamAV (Linux and other OpenSource OS's) and Audacity (available both in Linux and Windows))
If you're looking for OpenSource for Windows, this forum may not be the best place to look for your answers (Ubuntu is a Linux distribution). But I wouldn't really know a better place to point you to other than to do a searh on Google (or whatever other search-engine you prefer) for something like "Opensource forum" (without the quote-characters).

2. Next, if you really want answers for a Linux environment (standalone computer or network of computers), you should decide what is your main focus of concern:

A) You mentioned your high-security needs. The best place for this kind of discussion in this forum will be the "Security Decisions". You can discuss *where* you need that security starting on from there. ;)

B) You wondered how firewalls, ports and tunnels work. If you want to want deeper into this than beyond your security-concerns, then you could post a different post (besides the main one in the Security section) about those questions on the "Networking & Wireless" section.
I'm not too savy on this either but...
Most firewall software in Windows seems to focus on applications instead of ports. I.e. you authorize a given application to access your network or the whole Internet (and sometimes to be accessed by it as well) which is, IMHO, giving too much *carte blanche* to the application, specially because nowadays so many applications seem to want access to the Internet for almost no reason. Again, if you only grant them access to out-call (and get only the corresponding answer back), it should not be too risky, **provided you trust the application will not disclose information from your computer you don't want it to**. But if they are granted access to be called from the outside, then that application should be VERY robust, so as to prevent someone from the outside to use that application as an entry-door to your whole system (or even just to what the application controls, it may still be too much).
On ports and tunnels... I'm not so sure either but this is what I know:
Each computer has a port that is used for a given service. E.g. port 80 is used for HTTP communications (that's right, if you close port 80 to outgoing calls, you won't be able to surf the Web! lol). However closing port 80 to *incoming* connections is a must for every computer that does not host a webpage...
Linux standard firewall system is **iptables**. You'll never find its GUI (Graphical User Interface, a term not very know to Windows users though the Windows system itself does not work that differently than a Linux one in that aspect). iptables is base solely on **configuration files**! This file defines which IP addresses (each computer in a network has its own IP address though it is not always a fixed one; but there are never two computers with the same IP address at the same time) can be called to or called from to the computer the concerning iptables protects. iptables also defines which service (on what port) two or more computers can use to communicate (HTTP is one, FTP (File Transfer Protocol) is another, and so are POP3, SMTP and IMAP4 (mail services/protocols). You have the SIP service with its own port for voice and video conferencing too (though there are others, less specific, that may serve this purpose). And there are many, many others...

So basically, each port on a given computer is the gateway (or the door if you like) for a given service.

What are tunnels? Ah... tunnels! lol I know basically nothing about them. I do believe however they are connections, conduits, tunnels really!, between two (maybe more?) computers. One type of tunnel I often find in my readings is "a SSH (SecureSHell) tunnel, providing a secure line between computers, communicating through shell commands. There is also an SSH port BTW... ;)
But I am unsure if a tunnel is a synonim for every connection between the same port on different computers. I believe it is a consctuct, it is a construction built on top of the plain connection between the same port in different computers. It may also be that without that construct, the connection itself is refused and so, in practice, never exists (that should be the case for the SSH port, I believe). But I guess you can also build an encrypted/more-secure tunnel on top of any port-connection.
I am unsure if iptables can define tunnels too (but would guess it can though not on its own).

So as to not go to the hassle of manually editing the configuration file for iptable, there are several frontends you can use to ease that task, most of them NOT graphical. On the GUI end, common options are Firestarter (used in Ubuntu until release 8.10) and since 8.10 and in current 9.04, GUFW, the graphical frontend for... UFW... lol

Getting interested? Go to the Network and to the Security sections to get some proper definitive answers! :P


C) Finally, video does have the multimedia ring to it. But video chat definitely has the focus on the Networking aspect. ;)

Hope that helped somehow. :)


BTW, in my research years, I eagered for a Linux application compatible to the proprietary SPSS. We have PSPP now and it is pretty much up to the task (not all functions are implemented yet but I'd say most are and all the other data processing (building the tables-structure, defining the variables and their parameters, filling in the data and reading from / writing to SPSS files) is perfect. ;)

---

### Post by tgalati4 on 2009-08-22
"The internet is a series of tubes."

If you want to learn a little about networking, listen to Alan Hick's Network 101 talk that he gave recently at the Southeast Linux Fest.

[SELF Conference Audio Files]("http://www.archive.org/details/SouthEast_LinuxFest_2009")

[Class Notes]("http://carrier.lizella.net/networking_101.txt")

---

### Post by OpenSourceForAll on 2009-08-23
thank you all for your help, im going to move this query to the network part of the forum

---

