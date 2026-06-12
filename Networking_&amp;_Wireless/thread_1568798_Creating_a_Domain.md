---
title: "Creating a Domain"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by Jonny87 on 2010-09-05
I'm running Ubuntu 10:04 desktop on my desktop computer at home. As far as server features go, I've installed Samba and NFS.
I'm wanting to create a domain that I can connect my laptop (10:10 development) to and redirect the home folder and stuff to my account on the desktop. I also want have some form of off line caching so that I can access the same file when I'm not connected to the domain. And if possible I want to be able to join my wifes laptop running Win XP to the same domain and do the same with her account.

Can someone tell me what I need to install and point in the direction of how to go about it. I know about networking and so on, and with a shuv in the right direction I'll probably be able to work it out (unless it's incredibly complex).

---

### Post by MaindotC on 2010-09-05
Ok I think I can explain this to you but first I need to know - what is your degree of understanding with respect to network standards and protocols?  Are you studying in a degree programme such as information technology or computer science?

---

### Post by Jonny87 on 2010-09-05
No unfortunately I'm not doing a degree but I have been studying IT this year. As for what I know I'm to sure how to explain exactly what I do and don't know, networking is a wide area. Tell me or ask me about what I need to know for this and I'll let you know if I know it or not. If I don't know something I'm keen to learn. so either point me to some relevant pages or I'll look it up for my self. Any help would be appreciated.

---

### Post by MaindotC on 2010-09-06
Ok - you want to access a website or files on your laptop by typing in a name like mylaptop.com instead of typing in the ip address, right?  And you say you want to access a folder on your desktop - do you want to access them both using the same domain name?

---

### Post by Jonny87 on 2010-09-06
> **strAlan said:**
> Ok - you want to access a website or files on your laptop by typing in a name like mylaptop.com instead of typing in the ip address, right?  And you say you want to access a folder on your desktop - do you want to access them both using the same domain name?

The web page side of things isn't quite necessary. All I'm after is to be able to login on my laptop and have it login to a domain instead of just locally on the laptop. Something like Windows "Active Directory". I'm currently looking into LDAP but synaptic package manager has a few packages related to LDAP so I'm still trying to work out which one I need if any.

And while having the laptops are logged into "Domain" I want to have the main folders redirected to the desktop so that essentially when I browse my home folder on laptop it would be the same as browsing them on the desktop. Also if possible to have some form of off line caching so that if the laptop isn't connected to the domain it still has access to the files in those folders.

Basically something like an enterprise / corporate environment.

---

### Post by Jonny87 on 2010-09-06
I realize that I could possibly get these abilities in the server edition of of ubuntu but I'm limited on resources and want to keep the use of my desktop as it is. I just want to load it up with server features that will let me use it also as domain controller. But as I'm new to this stuff in linux I'm still not quite sure what packages I need and how to go about it.

---

### Post by fintos on 2010-09-06
Be careful while creating in order to avoid problems.

---

### Post by MaindotC on 2010-09-07
> **Jonny87 said:**
> The web page side of things isn't quite necessary. All I'm after is to be able to login on my laptop and have it login to a domain instead of just locally on the laptop. Something like Windows "Active Directory". I'm currently looking into LDAP but synaptic package manager has a few packages related to LDAP so I'm still trying to work out which one I need if any.

And while having the laptops are logged into "Domain" I want to have the main folders redirected to the desktop so that essentially when I browse my home folder on laptop it would be the same as browsing them on the desktop. Also if possible to have some form of off line caching so that if the laptop isn't connected to the domain it still has access to the files in those folders.

Basically something like an enterprise / corporate environment.

Ok - that's a little different than what I was thinking.  I know what you mean tho - you want a domain controller somewhere on your network (a home network I'm assuming) so when you log into your machine it contacts that domain controller for authentication and sets up a profile for you that contains network shares that are mapped to folders on your desktop.  Sorry if I misunderstood earlier.

Well, setting it all up is a project but as far as the domain name: if you want to access this domain outside of the network on which it resides, you will need to purchase a domain from a registrar like namecheap or godaddy.  Once you do that, the registrar will have a setting that basically asks "ok so when someone types in <your_domain.com> to what ip address do you want it pointed?" and that will usually be the public ip address of the domain controller.  If you will have a bunch of machines connected to your local network that's fine because we can deal with forwarding the domain requests (via NAT) to that particular machine later.

Once you get that set up with the registrar, then you'd want to install your domain controller.  I've not yet done this using OpenLDAP before but that would definitely be what you want to use.  What I did for a school project is set up an AD server, and then I used a client package called Likewise that would allow a non-winblows machine to send credentials to the AD server and log onto the domain.

There are some good videos on youtube for setting up OpenLDAP - mostly using a frontend called Webmin.  I've not actually set it up before but I've wanted to because I wanted to set up all the other services that would integrate with OpenLDAP - like a VPN server (poptop), authentication for protected web pages, file shares, sendmail, etc.  I'm sorry I can't tell you word for word how to do it, but I hope this points you in the right direction.  Perhaps it could be something we work on together.  Lemme know!

---

### Post by Jonny87 on 2010-09-07
> **strAlan said:**
> Ok - that's a little different than what I was thinking.  I know what you mean tho - you want a domain controller somewhere on your network (a home network I'm assuming) so when you log into your machine it contacts that domain controller for authentication and sets up a profile for you that contains network shares that are mapped to folders on your desktop.  Sorry if I misunderstood earlier.

Well, setting it all up is a project but as far as the domain name: if you want to access this domain outside of the network on which it resides, you will need to purchase a domain from a registrar like namecheap or godaddy.  Once you do that, the registrar will have a setting that basically asks "ok so when someone types in <your_domain.com> to what ip address do you want it pointed?" and that will usually be the public ip address of the domain controller.  If you will have a bunch of machines connected to your local network that's fine because we can deal with forwarding the domain requests (via NAT) to that particular machine later.

Once you get that set up with the registrar, then you'd want to install your domain controller.  I've not yet done this using OpenLDAP before but that would definitely be what you want to use.  What I did for a school project is set up an AD server, and then I used a client package called Likewise that would allow a non-winblows machine to send credentials to the AD server and log onto the domain.

There are some good videos on youtube for setting up OpenLDAP - mostly using a frontend called Webmin.  I've not actually set it up before but I've wanted to because I wanted to set up all the other services that would integrate with OpenLDAP - like a VPN server (poptop), authentication for protected web pages, file shares, sendmail, etc.  I'm sorry I can't tell you word for word how to do it, but I hope this points you in the right direction.  Perhaps it could be something we work on together.  Lemme know!

You don't happen to know what packages specifically to install for LDAP (preferably a GUI) do you? As I said earlier, I've looked in Synaptic but there are quite a few that have something to do with LDAP and I don't want to waste time and download getting stuff that I don't need.

And year if you would like to work with me to accomplish this I'd be more than happy to have a set person to bounce ideas off. 

Theres another issue though, I may need to start another thread for this, but I've found that networking features seem to be unreliable. Some days I can browse from my desktop comp to the laptop (and vise versa) fine, but other days (like right now) it just keeps giving errors. Is this common? do others use some thing else? I'm using SAMBA as my main utility for sharing folders mainly because I have an XP laptop and a win 7 comp on the network as well.

---

### Post by MaindotC on 2010-09-07
Yeah that's a separate thread issue.  What you should do is use [this guide](http://ubuntuforums.org/showthread.php?t=25557) for troubleshooting network connections.

I don't know precisely what packages to install for OpenLDAP but it's not something you do in 10 minutes.  I googled "openldap domain controller" and most of the tutorials refer to Samba being the domain controller which I guess is one of the prevalent ways of accomplishing this.  What I would advise is finding a tutorial and then building it on a VM.  If everything works great, you can map the VM as your domain controller or replicate the process to your host machine.

---

### Post by Jonny87 on 2010-09-07
> **strAlan said:**
>   What I would advise is finding a tutorial and then building it on a VM.  If everything works great, you can map the VM as your domain controller or replicate the process to your host machine.

Good idea. I have VMware installed so I'll do just that. Once I have a working system I'll use that process to set it up on my main machine. LOL by that time 10:10 will probably be out so it would be a good reason for a clean install. If I don't decide to stick with 10.04.

Oh and thanks for the link, I'll check it out now.

---

### Post by d3v1150m471c on 2010-09-07
out of curiosity, what's the domain for? you don't need it to share folders from your laptop. you can do this in an easy secure manner as well.

---

### Post by Jonny87 on 2010-09-09
> **d3v1150m471c said:**
> out of curiosity, what's the domain for? you don't need it to share folders from your laptop. you can do this in an easy secure manner as well.

Sorry for the late reply.
It was originally an idea to keep the folders synced together but now its just for the sake of it. After having the idea I still thought it would be good to for the experience if I was able to get something llike this working.
I'm currently working on getting a script working using the cp command with update switch to sync the folders.

---

