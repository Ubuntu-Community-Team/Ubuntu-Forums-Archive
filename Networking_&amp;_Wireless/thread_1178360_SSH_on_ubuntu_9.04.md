---
title: "SSH on ubuntu 9.04"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by CynicalPsycho on 2009-06-04
I'm curious about using SSH to securely connect remotely to other computers...

I've done a bit of googling but I can't seem to find any real answers for my questions...

So I'll ask you guys...

Does anyone here know where I can find info on what I need to get SSH up and running between 2 computers running ubuntu?

I understand SSH is just a protocol and that I need a program such as openSSH to get it running but is that all that's involved?

I've briefly tried to get it working between mine and a friends computer to no avail... we kept getting an error about there being no route...

We were trying to ssh over a wireless internet connection, is there anything special involved in this or should it work the same as it would with any other lan of computers?

does anyone here have any experience with this protocol that could give me a bit of guidance?

---

### Post by x22 on 2009-06-04
well, this should be easy: here's some ideas:

1. can you connect the two computers with a cable?
   introduce wifi after that works

2. suppose computer A has IP-address 192.168.1.1 but
   computer B has IP-address 192.168.1.2: then try
   A: "ping 192.168.1.2"
   B: "ping 192.168.1.1"
   you should get responses: if not, at least one
   network interface isn't set up correctly.

3. what error messages? "no route to
   host" is a networking problem, see above.

4. is each machine running the daemon "sshd"?

---

### Post by CynicalPsycho on 2009-06-04
> **x22 said:**
> well, this should be easy
Yeah I figured it would be too...

> **x22 said:**
> 
1. can you connect the two computers with a cable?
   introduce wifi after that works
Yea, I'll have to try this one... but I don't really see the difference if we're connected through to the router... wireless or cable, it should be the same...

> **22 said:**
>  
2. suppose computer A has IP-address 192.168.1.1 but
   computer B has IP-address 192.168.1.2: then try
   A: "ping 192.168.1.2"
   B: "ping 192.168.1.1"
   you should get responses: if not, at least one
   network interface isn't set up correctly.
yeah we could ping each other no problem, we just got the error of there being no route...

> **x22 said:**
> 
3. what error messages? "no route to
   host" is a networking problem, see above.... no solution

> **x22 said:**
> 
4. is each machine running the daemon "sshd"?
this I do not know about... can you tell me more?

---

### Post by Iowan on 2009-06-04
[Here]("http://www.unixtutorial.org/2009/05/ubuntu-ssh-how-to-enable-secure-shell-in-ubuntu/") is one How-To I found (but haven't read). [This]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html") one is about setting up SSH server - which one (or both) machines will need to accept connections. [Another ]("https://help.ubuntu.com/community/SSH/OpenSSH/InstallingConfiguringTesting") one on installing the server.  A [How-To]("https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo") on connecting.  That should be enough to start with...

---

### Post by dmizer on 2009-06-05
Two computers.

Computer1 is remote. Computer2 is the one you are using.

If you want to connect to Computer1 from Computer2 with ssh, you must have an ssh server installed on Computer1. You can install an ssh server with this command:
```
sudo apt-get install openssh-server
```

Once openssh-server is installed on Computer1, then you can connect from Computer2 with this command:
```
ssh [COLOR="Red"]user[/COLOR]@[COLOR="DarkGreen"]computer1[/COLOR]
```
where:
[COLOR="Red"]user[/COLOR] = computer1's username
[COLOR="DarkGreen"]computer1[/COLOR] = computer1's IP address.

It becomes more complex if you want to do the same across the internet rather than within your own LAN, because you'll have to do things like hardening your SSH server as well as port forwarding through your router.

---

