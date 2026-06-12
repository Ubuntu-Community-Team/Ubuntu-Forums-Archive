---
title: "remote server"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by Bray90820 on 2012-01-31
i have ubuntu 11.10 home serverand i want to map it so i can use it away from home and have it show up as a regular hard drive

---

### Post by Lars Noodén on 2012-01-31
A very secure way to do that would be to use SSHFS.  It uses SFTP so if you already have the package OpenSSH-Server installed, then you are all set on the server side of things.

On the client side, you need to install the package sshfs and then add yourself to the group 'fuse'

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

There are also other HowTos and guides around the net explaining the same method and some advanced tricks.

---

### Post by Bray90820 on 2012-01-31
do i enable ssh on the server side and sshfs on the client side

---

### Post by Bray90820 on 2012-01-31
does sshfs work over wan

---

### Post by Lars Noodén on 2012-02-01
> **Bray90820 said:**
> do i enable ssh on the server side and sshfs on the client side

Yes.

> **Bray90820 said:**
> does sshfs work over wan

Yes, that's why I proposed it.  If your connection is LAN-only then there are more options.  But SSH, or specifically SSHFS, is a very practical and secure way to mount remote systems.

---

### Post by Bray90820 on 2012-02-01
how would i go about mounting it over wan i tried a few things earlier but all i could get was mounting it over lan

---

### Post by Lars Noodén on 2012-02-01
You would mount it the same over WAN as for LAN.  

Unless if you have NAT.  Then your router must forward port 22 (SSH) to the server so that you can connect from outside.  If that is the case there should be some setting on your router to forward ports.  The details vary from model to model.  Once you have port forwarding, you can use SSHFS to connect to the external address of your router and it will cause you to connect to your server.

---

### Post by Bray90820 on 2012-02-02
i tried that but for some reason it ant working

---

### Post by Lars Noodén on 2012-02-03
You could check to see if your ISP is blocking port 22 (SSH) :

[http://canyouseeme.org/](http://canyouseeme.org/)

---

### Post by Bray90820 on 2012-02-03
wouldn't i have to create a ssh tunnel

---

### Post by Lars Noodén on 2012-02-03
A tunnel is something different.  SSHFS is really SFTP, which is part of SSH, so all you need is the SSH connection and SSHFS will work for you.

---

### Post by Bray90820 on 2012-02-04
well what i am trying to do is connect to it away from my house

---

### Post by Lars Noodén on 2012-02-04
What about the question in post #9?  You need to be able to connect to SSH from the outside.  The setup is usually like this:

```

Computer1 --- Internet --- Home Router --- Home Computer

```

Usually the home router has an externally visible address and usually the home computer is on a private subnet using NAT.  So in order to reach the home computer from the computer1 (away), the router has to forward SSH from its external address to the home computer.

---

### Post by Bray90820 on 2012-02-04
i am so confused what do i do i know i can connect to port 22

---

### Post by Lars Noodén on 2012-02-04
What about the question in [#9](http://ubuntuforums.org/showpost.php?p=11660960&postcount=9) above?  Is port 22 open?  If so then you need to check your router's settings.

---

### Post by Bray90820 on 2012-02-04
when i try to check if port 22 is open i get this error 

Error: I could not see your service on <ip address> on port (22)
Reason: Connection timed out

what i am thinking is my router might not work because it;s an airport extreme

---

### Post by Bray90820 on 2012-02-06
so i bought a new router and the port is open but i cant seem to access it remotely

---

### Post by CharlesA on 2012-02-06
Are you sure you have your port forwarding set up correctly? If it's correct, check to make sure port 22 isn't blocked by your ISP.

---

### Post by Bray90820 on 2012-02-06
should i connect the same way locally as i do remotly

---

### Post by Bray90820 on 2012-02-06
i am in it turned out i was using my computers ip address instead of my routers

---

### Post by CharlesA on 2012-02-06
> **Bray90820 said:**
> i am in it turned out i was using my computers ip address instead of my routers
That would do it. If you want to access it remotely you'd need your external IP address.

---

### Post by Bray90820 on 2012-02-07
Solved

---

