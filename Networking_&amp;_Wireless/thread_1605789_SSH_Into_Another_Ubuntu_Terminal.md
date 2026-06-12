---
title: "SSH Into Another Ubuntu Terminal"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by Shadow21 on 2010-10-25
I'm trying to SSH into my desktop computer that is also running Ubuntu. I'm running the command:

```
ssh ComputerIP
``` 

and I figured that wouldn't work because I didn't specify anything else (such as a password) because I don't know how to specify anything else.

How do I SSH into another Ubuntu Terminal?

---

### Post by Shadow21 on 2010-10-30
bump

---

### Post by holiday on 2010-10-30
you have to log in to an account on the server so

$ ssh shadow@ComputerIp

If this is something you're going to do a lot, google on ssh empty passwords and there is some simple instruction.

---

### Post by srhart on 2010-10-30
Hi, I assume you are running an SSH server on the destination machine? This is not enabled by default on a desktop installation. Install it by:
sudo apt-get install openssh-server
on the destination machine

Once that's done you need to:
ssh user@machine
(if you dont specify user information it will default to the same username as your current environment - you need to use a valid user account on the destination machine)

in your case e.g:
ssh Shadow21@ComputerIP

It will pause while key exchange occurs then notify you that you havent connected to this machine before would you like to store the credentials, answer yes

It will then ask for the password of the user on the destination machine, answer this correctly and you should be connected.

Good luck
Simon
------------------------
[www.L3n.co.uk]("http://www.L3n.co.uk") L3n Network Support - Contact L3n for voice and data network design, supply, installation and support - based in Cambridge UK

---

### Post by tonyrueb on 2010-10-30
ssh <username>@<computer_address>
it will prompt you for a password

---

### Post by elico on 2010-10-30
it's not a must to enter the username and password.
just make sure that the firewall allowing ssh and the ssh installed up and running.

---

### Post by Iowan on 2010-10-30
> **srhart said:**
> Hi, I assume you are running an SSH server on the destination machine? This is not enabled by default on a desktop installation. Install it by:
sudo apt-get install openssh-server
on the destination machine
+1 Ubuntu comes with several clients pre-installed (SSH is one), but the server must be installed on the machine you wish to access.

---

### Post by v1ad on 2010-10-30
also that if is on the same local network.

ssh username@LocalIpaddress

if connected directly to modem, or remoting off a different network.

shh username@ipaddress

also if you are connecting from a different network you will need to forward the port 22 from the router to pc.

this will install the client/server

sudo apt-get install ssh

---

### Post by NertSkull on 2010-10-30
Also, in case you don't know, make sure you look at securing the server.

There are lots of great ways to do this, most importantly is using SSH keys (and maybe running on an alternative port).

But keys, in my opinion, are the most important thing to do when setting up a new SSH server.

There are LOTS of tutorials on how to do that out there.  If you need I have probably 7 or 8 bookmarked I can look up that got me going.  

SSH fast became one of my favorite parts of linux.

---

### Post by Shadow21 on 2010-10-31
> **srhart said:**
> Hi, I assume you are running an SSH server on the destination machine? This is not enabled by default on a desktop installation. Install it by:
sudo apt-get install openssh-server
on the destination machine

Once that's done you need to:
ssh user@machine
(if you dont specify user information it will default to the same username as your current environment - you need to use a valid user account on the destination machine)

in your case e.g:
ssh Shadow21@ComputerIP

It will pause while key exchange occurs then notify you that you havent connected to this machine before would you like to store the credentials, answer yes

It will then ask for the password of the user on the destination machine, answer this correctly and you should be connected.

Good luck
Simon


I installed the server so it works now.

Thanks!

---

### Post by Iowan on 2010-10-31
If you'd be so kind s to mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). others might benefit from your experience... :)

---

