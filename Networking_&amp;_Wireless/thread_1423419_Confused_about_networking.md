---
title: "Confused about networking"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by sabersong on 2010-03-06
I've searched for an answer for a couple weeks.  I have two identical computers, both running Kubuntu 9.10, sharing a broadband internet connection through a router, to which they are both wired. They both also have wireless capability.  But I can't get them to communicate with one another.  I can find info on sharing the printer and sharing files, but everything I find assumes that you already have the computers set up on a network.  Apparently, I don't, and can't find simple instructions on how to set up the network.  I want to be able to share the printer and files between the two computers and continue to share the broadband connection through the router.  Can anyone point me to the information I need?  Please note that I'm not what you'd consider knowledgeable when it comes to networking, so simple, easy to follow how-tos would be best.  Thanks.

---

### Post by Iowan on 2010-03-07
Can you **ping** from one machine to the other? Easiest way to check is to open a terminal (Applications>Accessories>Terminal) and enter:```
ifconfig -a
``` Do this on each machine to learn it's IP address (probably 192.168.X.X). (another option is to use the **ip link** command from a terminal). Once you know the address of the both machines,  you can (from the terminal, again):```
ping <ip.of.other.computer>
``` You would (of course) be using the address you found earlier.

---

### Post by sabersong on 2010-03-07
Thank you for taking the time to respond.  Yes, I can ping each computer from the other.

---

### Post by Iowan on 2010-03-07
The networking part of your problem would appear to be solved... I haven't used Kubuntu, but I suspect the same file sharing options exist. Samba will let you do file/printer sharing. [NFS]("http://ubuntuforums.org/showthread.php?t=249889") is another filesharing option between Linux machines.

---

### Post by sabersong on 2010-03-07
Ok ... thank you.  Now I just need to figure out how to use NFS or Samba.  The NFS link you included should help.  Thank you.

---

