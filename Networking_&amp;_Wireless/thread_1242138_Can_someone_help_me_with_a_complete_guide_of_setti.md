---
title: "Can someone help me with a complete guide of setting up remote desktop?"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by adam93 on 2009-08-16
I've spent hours on end trying to do this, and have failed. I've searched google and the sort, but I just could not do it. Could someone please help me? If you haven't guessed yet, I'm new to Linux.

---

### Post by dmizer on 2009-08-16
System > Preferences > Remote desktop > put a check mark in "Allow other users to view your desktop"

---

### Post by Ranko95 on 2009-08-16
its actually very easy. You can configure it from System > Preferences > Remote desktop. Then all you need is some vnc or rdp client on the guest computer. I have even remotely logged in on my ipod touch! good luck!

---

### Post by adam93 on 2009-08-16
yeah I tried that, it did not work. It says that its only accessible over the local network

---

### Post by dmizer on 2009-08-16
> **adam93 said:**
> It says that its only accessible over the local network

Which is the way it should be. You should not be able to access remote desktop via the internet as the RDP protocol is not written to be secure over an open internet connection.

You can try some alternatives like piping the RDP through an SSH tunnel. Is there something in particular you're needing to do? There may be some better alternatives than remote desktop. Remote desktop is usually too bandwidth intensive to be used over the internet anyway.

---

### Post by adam93 on 2009-08-17
Oh, I thought that just meant that it wouldn't work on any other computer.
So if I have all that worked out, how do I get it working?

---

### Post by dmizer on 2009-08-17
> **adam93 said:**
> Oh, I thought that just meant that it wouldn't work on any other computer.
So if I have all that worked out, how do I get it working?

Just use the RDP client of your choice and enter the Ubuntu computer's IP to connect.

---

### Post by adam93 on 2009-08-17
I tried that and it just didn't work. I think it had something to do with port forwarding and making a static IP address

---

### Post by pdc124 on 2009-08-17
whats your network setup ?

if its 
www--> router/firewall-->desktop 
and you want to connect from ww then you need to portforward 5900 from your  router to your desktop

---

### Post by adam93 on 2009-08-17
yeah thats what i thought, but don't I have to make my desktop have a static IP to do that?

---

### Post by dmizer on 2009-08-17
> **adam93 said:**
> yeah thats what i thought, but don't I have to make my desktop have a static IP to do that?

It depends on your router's capabilities.

As I said before. This:

www--> router/firewall-->desktop 

Is a terrible idea. Remote desktop is NOT meant for this. Even if you've taken the necessary precautions, the only thing that stands between you and having your desktop completely owned by a hacker is an easily crackable password, and that's only if you've even configured password protected remote desktop.

Besides, even if you DO manage to get remote desktop properly fowarded across the internet, it will be unusably slow.

What is it that you're trying to do? If you tell us what you need RDP for, there's probably a MUCH more secure way of doing what you need to do.

---

### Post by MeumFidet on 2009-08-17
> **dmizer said:**
> It depends on your router's capabilities.

As I said before. This:

www--> router/firewall-->desktop 

Is a terrible idea. Remote desktop is NOT meant for this. Even if you've taken the necessary precautions, the only thing that stands between you and having your desktop completely owned by a hacker is an easily crackable password, and that's only if you've even configured password protected remote desktop.

Besides, even if you DO manage to get remote desktop properly fowarded across the internet, it will be unusably slow.

What is it that you're trying to do? If you tell us what you need RDP for, there's probably a MUCH more secure way of doing what you need to do.


hi Dmizer,

I too would like to know how to get remote desktop up and running.  I intend to access a virtual server via the internet and my command line skills are not very good (linux newbie) so I reckoned a remote desktop connection would allow me to sort out some of the more tricky problems when they arose.  

I take your point about the security, but couldn't I start the vnc service by ssh, use the remote desktop and then stop the service once I had done what need to be done?

Access to the 9.04 server is by ssh only, with tightvncserver installed and accessed via putty on vista.  Putty connects, but vncviewer gives a "could not connect to server" error.

Cheers,

MF

---

### Post by dmizer on 2009-08-17
> **MeumFidet said:**
> hi Dmizer,

I too would like to know how to get remote desktop up and running.  I intend to access a virtual server via the internet and my command line skills are not very good (linux newbie) so I reckoned a remote desktop connection would allow me to sort out some of the more tricky problems when they arose.  

I take your point about the security, but couldn't I start the vnc service by ssh, use the remote desktop and then stop the service once I had done what need to be done?

Access to the 9.04 server is by ssh only, with tightvncserver installed and accessed via putty on vista.  Putty connects, but vncviewer gives a "could not connect to server" error.

Cheers,

MF

Most server tasks are done via the CLI anyway, so even if you do have a GUI, you will find yourself in the command line most of the time anyway. And most especially if you find yourself having to solve some sort of problem.

Why not just install a web administration tool like ebox or webmin. That way, you can ssh in with a proxy switch and securely access all your system settings via a web based point and click interface.

Or, rather than webmin, install a web administration tool specifically for the task you wish to do.

---

### Post by MeumFidet on 2009-08-18
> **dmizer said:**
> Most server tasks are done via the CLI anyway, so even if you do have a GUI, you will find yourself in the command line most of the time anyway. And most especially if you find yourself having to solve some sort of problem.
 
Why not just install a web administration tool like ebox or webmin. That way, you can ssh in with a proxy switch and securely access all your system settings via a web based point and click interface.
 
Or, rather than webmin, install a web administration tool specifically for the task you wish to do.
 
 
Sound advice!  Thanks Dmizer, I will go away and have a look at some web admin programs - Cheers!
 
MF

---

### Post by adam93 on 2009-08-21
Sorry about the long reply. 
Anyways, what I would like to do is access my desktop from anywhere with an internet connection.

---

### Post by dmizer on 2009-08-21
> **adam93 said:**
> Anyways, what I would like to do is access my desktop from anywhere with an internet connection.

When you access your desktop, what exactly do you intend to do? In other words, is there some particular reason you need a complete desktop, or would one program (Firefox for example) be sufficient?

---

