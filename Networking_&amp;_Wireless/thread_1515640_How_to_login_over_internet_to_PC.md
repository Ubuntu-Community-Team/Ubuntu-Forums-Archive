---
title: "How to login over internet to PC"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by lleming on 2010-06-22
So i want to help my friend to setup Ubuntu. Both of us in the internet. Of couse both of us behind NAT. Of couse both of us doesnt have access to router. So is anywhere available instruction how i can join to his terminal session.

---

### Post by dozdozez on 2010-06-22
> **lleming said:**
> So i want to help my friend to setup Ubuntu. Both of us in the internet. Of couse both of us behind NAT. Of couse both of us doesnt have access to router. So is anywhere available instruction how i can join to his terminal session.

Your friend has to start the ssh server on his computer: sudo /etc/init.d/ssh.
After that, he has to open a port on his router configuration and enroute it to the port 22 on his machine. (Asuming that his ssh server is using the default port 22 on his computer) 
It is not a good idea to open the port 22 of your router to do this, cause it is the standard port for ssh and someone could try to access by ssh triying several passwords.

Then to access to the computer of your friend just do:
 ssh -p router_port user@ip

Disabling direct root acces via ssh is strongly recomended for security issues. (Once logged in, you use the su command if needed.)
Better use a strong pass.
Once the job is done, turning down the ssh connection is a good idea.

---

### Post by pricetech on 2010-06-22
> **dozdozez said:**
> After that, he has to open a port on his router configuration and enroute it to the port 22 on his machine.

OP already stated he has no access to the router.

---

### Post by dozdozez on 2010-06-22
Ups!

I don't know what to say, has he any modem so he can connect the pc directely to internet?

If not, I don't know if there is any way for you to connect to his machine. Sorry.

---

### Post by Yarui on 2010-06-22
If you are on a router you have to forward the ports for ssh to work.  If you don't have access to the router it's unlikely you are going to find a way to ssh into a machine on the network.  Try asking the person who does have administrative access to the router to forward a port for your ssh session.  If they don't want to forward port 22 for you, they may be willing to forward a different port for you, in which case you will need to change your ssh server's port from 22 to something non-standard.  If you can't get a port forwarded for you, I think you are out of luck.

---

### Post by drdos2006 on 2010-06-22
Have a look at TeamViewer, you need the server software on one computer and client software on the other computer.

regards

---

### Post by foxmulder881 on 2010-06-22
As above, TeamViewer will do all you need. Remote networking, file transfers and vpn. I use it on my Windows server and desktop and it's now available on Linux too.

---

### Post by dozdozez on 2010-06-23
Ok, here is another idea:

1.- In his machine he starts the ssh daemon
2.- You start the ssh daemon in your computer
3.- He connects to your computer via ssh, forwarding his port 22 to another port on your computer:
       ssh user@ip -R 2055:localhost:22
4.- Now you can connect to his port 22 on 2055 of your computer:
     ssh user@localhost -p 2055

I think it must work.

---

### Post by lleming on 2010-06-23
Thanks to everyone. This is what i was thinking before that without at list one real external IP i cannot connect to another PC behind NAT. Unfortunately i cannot effort such service as private server on amazon.
So i have one more question is it safe to use services like teamviewer or logmein?

---

### Post by lleming on 2010-06-23
> **dozdozez said:**
> Ok, here is another idea:

1.- In his machine he starts the ssh daemon
2.- You start the ssh daemon in your computer
3.- He connects to your computer via ssh, forwarding his port 22 to another port on your computer:
       ssh user@ip -R 2055:localhost:22
4.- Now you can connect to his port 22 on 2055 of your computer:
     ssh user@localhost -p 2055

I think it must work.


Problem that i am behind NAT  thats why i have something like 192.168.3.135
He is the same. So we cannot see each other. We have diff providers.  Even in diff countries

---

### Post by dozdozez on 2010-06-23
Umm...

true, at least one of you must have access to the router.
bad luck :-(

---

### Post by foxmulder881 on 2010-06-24
So what was wrong with TeamViewer? It'll bypass all the aformentioned connection problems.

---

### Post by lleming on 2010-07-03
> **foxmulder881 said:**
> So what was wrong with TeamViewer? It'll bypass all the aformentioned connection problems.


Yeap I am using teamviewr by the way its free for personal use

---

