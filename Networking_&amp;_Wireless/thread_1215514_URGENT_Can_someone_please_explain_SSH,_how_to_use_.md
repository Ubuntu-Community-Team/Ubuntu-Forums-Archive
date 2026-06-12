---
title: "URGENT: Can someone please explain SSH, how to use it, and it's point?"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by ADyingSoul on 2009-07-17
I was working on my box with my jailbroken iPod touch sitting beside me (the fact that it's jailbroken isn't very important. only know that by doing so I have access to a terminal on my iPod) and I was messing around.

I came across SSH... and (I think) I connected to my iPod through my computer. Why would someone want to do something like this and what would be the purpose?

---

### Post by VastOne on 2009-07-17
> **ADyingSoul said:**
> I was working on my box with my jailbroken iPod touch sitting beside me (the fact that it's jailbroken isn't very important. only know that by doing so I have access to a terminal on my iPod) and I was messing around.

I came across SSH... and (I think) I connected to my iPod through my computer. Why would someone want to do something like this and what would be the purpose?

Can you explain exactly what it is you did and what your questions is? I do not understand what it is you are asking.

---

### Post by hetx on 2009-07-17
In order to move files over SSH using SCP eg

Haven't done it myself so I can't tell you what else it's good for =D

---

### Post by ADyingSoul on 2009-07-17
I don't even really understand what I did. Basically it's this.
1. I found out I could use SSH on my iPod touch.
2. I followed instructions (since I don't really know what SSH is) to connect my computer to my iPod.
3. Now what?

Here is what the terminal on my PC looks like

nick@lucky:~$ ssh root@192.168.1.3
root@192.168.1.3's password:
Nicks-iPod-touch:~ root#

Basically what I'm asking is... what the hell did I just do? :confused:

---

### Post by martinbaselier on 2009-07-17
Ssh stands for secure shell. It's normally used for encrypted connections over a network, so you can start a terminal session on the remote machine.
scp is a version of cp to copy files over a network. It uses ssh for data transfer. **man ssh** and **man scp** will give you more information about their options. 

> 
nick@lucky:~$ ssh root@192.168.1.3
root@192.168.1.3's password:
Nicks-iPod-touch:~ root#
Basically what I'm asking is... what the hell did I just do?  

You just logged into your ipod and now you can execute commands on it, just like you would normally do in a terminal on your local computer. I believe apple uses a version of BSD on it. I don't know which commands are available. **ls** would give a directory listing. Other available commands are probably in /bin/, /sbin/, etc The structure of the filesystem is quite similar to that of linux.

btw: I wonder what's so urgent about your question. You could have just looked on [wikipedia](http://en.wikipedia.org/wiki/Ssh) and you would have found the same information there.

---

### Post by jonobr on 2009-07-17
Urgent is when your company file server goes belly and your backup is corrupt.

You cant find that on the wiki,

Respectfully, I would recommend investigate and read first, backup data before doing anything  and experiment based on your findings,


This forum has a lot of posts from people who act first and then investigate second.

---

