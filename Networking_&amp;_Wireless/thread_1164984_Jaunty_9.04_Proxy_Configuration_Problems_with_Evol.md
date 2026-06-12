---
title: "Jaunty 9.04 Proxy Configuration Problems with Evolution"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by slick666 on 2009-05-20
I recently upgraded through re-installation from 8.04 to 9.04. I'm now having networking issues that all seem to be related to the proxy configuration. I had this working on 8.04 and I don't understand why they don't work on 9.04.

The system is at work where I don't control the network but up till this point the system was interfacing fine. We have a proxy that all machines use for all traffic to the Internet (http, https, ftp, etc.). What I had done previously is take the text from IE on my other machine and put it in the **Autoconfiguration URL** of the network proxy configuration. There is a new button name **Apply System-Wide** that I also now click and it asks me for my password. The problems I'm getting are this.

Firefox works just fine
Apt-get works
and some others

Evolution does not
I'm configuring it from a backup configuration I saved from my 8.04 system. I'm using the MS Exchange settings and when I enter the OWA URL it gives me the error

**"Could not connect to server, Make sure the URL is correct and try again"** 

I can use that URL in firefox to access the mail just fine so I don't see the problem. If instead of putting in the https I put  in http I get a different error.

**"Could not configure Exchange account because an unknown error occured. Check the URL, username, and password, and try again."**

On of the things I suspect is that the auto configuration does not specify and https configuration explicitly. When I download the .pac file it only defines an http proxy. Everything is supposed to go through it but I'm wondering if evolution is using it for http access and not https access.

I'm stuck on debugging this so if anyone has an Idea please share. I also looked for similar threads in the networking folder but I didn't see any. If there is one I've missed please direct me to that thread.

Thanks

---

### Post by slick666 on 2009-05-21
Bump Bump

New update. I WAS able to get the system to log on by:
[LIST=1]
[*]Set the network settings of evolution to a direct connection (or in otherwords do not use the proxy configuration of the system)
[*]Replace the URL with the ip address
[/LIST]

So far I've been able to "log in" and the system has been able to download all my messages. I'm still convinced that while firefox can resolve https addresses evolution cannot. 

Has anyone else run into this problem?
Does anyone else have an idea of what else the problem might be?

---

### Post by PhilFromIT on 2009-05-22
> **slick666 said:**
> Bump Bump
 

New update. I WAS able to get the system to log on by:[LIST=1]
[*]Set the network settings of evolution to a direct connection (or in otherwords do not use the proxy configuration of the system)
[*]Replace the URL with the ip address
[/LIST]
So far I've been able to "log in" and the system has been able to download all my messages. I'm still convinced that while firefox can resolve https addresses evolution cannot. 
 
Has anyone else run into this problem?
Does anyone else have an idea of what else the problem might be?
 
[COLOR=black][FONT=Verdana]I am running 9.04 Netbook-remix and am having similar issues with proxies and Evolution. I cannot get it to connect to Gmail through my proxy here at work. I have tried configuring the proxy both at the system level and in Evolution preferences. When it attempts to retrieve the emails it gets a "Host lookup failed: pop.gmail.com: Name or service not known".  I use the same proxy settings in Firefox with no issues.  (Although, even FireFox does not seem to recognize Network Proxies at the system level.)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][/FONT][/COLOR]

---

### Post by slick666 on 2009-05-23
I've opened up a bug under launchpad

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/379055]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/379055")

What I ended up doing was configuring the system with **no** proxy and everything worked fine. This is because the exchange server is an internal web-page. With no proxy evolution is able to access https pages no problem.

>  I cannot get it to connect to Gmail through my proxy here at work. I have tried configuring the proxy both at the system level and in Evolution preferences. When it attempts to retrieve the emails it gets a "Host lookup failed: pop.gmail.com: Name or service not known".

PhilFromIT, I expect you are having the same problem. You may be able to access your gmail account but only through http. If I'm not mistaken gmail has both an http and https login and I would think evolution is programmed to use https.

I wish I knew a work around but my work blocks gmail all together. My one thought is to make my own proxy locally and use it to ferry the https and ftp traffic back and forth but I've never done that before but it should like it would work.

---

### Post by slick666 on 2009-05-26
Run into another problem that I think is related and I'm hoping for some feedback here. I can't seem to get the the address book working under evolution.

The error is
> 
Error loading address book.
This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.


If I execute evolution from the command line I get the following error on my console
> ** (evolution:11593): WARNING **: LDAP authentication failed (0xffffffff (Can't contact LDAP server))

I was hoping someone could give me an idea of how to start addressing this problem. I can't tell if the server can't be reached or if the authentication isn't working. Any input would be helpful.

---

### Post by X1R1 on 2009-11-25
Count me in for the same problem. All works under the proxy, except evolution and pidgin, no idea why, If I use emesene it goes trough and I can talk with everyone, with pidgin I cant connect:

> Connection error from Notification server:
HTTP proxy connection error 502

And in evolution:

> Host lookup failed: imap.gmail.com: Name or service not known

everything else works fine, I hope there is a solution for this. I think that the pidgin and evolution problems are very closely related.

---

### Post by bronkeydain on 2010-05-27
Same problem here on 10.04 LTS. I have a proxy at work. Everything works on global proxy settings apart from Evolution. 

It is not a DNS problem as when I put in my POP3 servers IP address in the settings I still get this ERROR:  Could not connect to 64.16.162.145: Connection timed out (IP address not real in this example)

I also tried Thunderbird mail and it has the same problem, looks like the mail protocol is not getting past the proxy. Any tips or tricks anyone?

---

### Post by rohit raj on 2010-06-28
I am also facing the same problem. Everything works fine. Pigdin also works fine. But evolution gives error message host lookup failed : pop.gmail.com name or service not known

---

### Post by rohit raj on 2010-06-28
Meanwhile i am using ubuntu 9.04. I was using evolution 2.26.1. I upgraded to evolution 2.28.1 but the same error persists

---

### Post by rohit raj on 2010-06-28
I figured out the solution for it by myself. I had not put domain name server in /etc/resolv.conf file. Without it everyother application works 
well except evolution

---

### Post by rohit raj on 2010-06-29
When i restart ubuntu /etc/resolv.conf file gets reset. The domain name server entry that i put up gets deleted. What i have to do to make the entry permanent

---

### Post by slick666 on 2010-06-29
When I updated from 9.04 to 10.04 all the proxy issues went away. I had to update my server's address because internally it changed but everything works great with the exception of booking resources.

---

