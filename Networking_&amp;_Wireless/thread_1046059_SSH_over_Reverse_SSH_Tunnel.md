---
title: "SSH over Reverse SSH Tunnel"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by mjrmua on 2009-01-21
I have the following setup:

(Machine A) -- (router A) -- (Internet) -- (router B)--(Machine B)

I would like to be able to SSH from Machine A to Machine B.

Both routers NAT'ing, and port forwarding port 22.  

I'm trying to establish a reverse SSH tunnel from B to A, and then ssh from A to B over the tunnel (Because I want to turn off port forwarding on routerB).  As follows:

MachineB$ ssh -NT -R 1234:localhost:22 -p 22 username@<routerA_public_IP>
MachineA$ ssh username@localhost -p 1234 

This works fine if I put Machine A and B on the same network. 

But if I move B behind its router: 
-The tunnel is established correctly
-I can still ssh A->B, and B->A
but when I try to ssh from A to B over the tunnel I get the folowing error:   

MachineA$ ssh username@localhost -p 1234 
ssh_exchange_identification: Connection closed by remote host

Any ideas on what's going wrong here?

---

### Post by zzzisgood on 2010-01-29
I came across the same problem, remember to install ssh server , eg. openssh-server, on both machines if you want the bi-direction ssh working. 

The solutions on [http://ubuntuforums.org/showthread.php?t=1011934&page=1](http://ubuntuforums.org/showthread.php?t=1011934&page=1) did not solve my problem, instead, I had to remove and reinstall openssh-server to get it work, I don't know why, but reinstallation solved the problem.

---

### Post by llawwehttam on 2010-01-29
I agree. you will need to:
 
```
sudo apt-get install openssh-server
```
 
on the machine not accepting connections then it should work.

---

### Post by Dynatoz on 2010-05-26
> **llawwehttam said:**
> I agree. you will need to:
 
```
sudo apt-get install openssh-server
```on the machine not accepting connections then it should work.
I'm trying to do the same thing.

I sometimes require logging into my work computer from home, using a reverse ssh tunnel. My work computer is using plink.exe (Windows XP) with the command line: plink.exe -R 10000:localhost:22 -P 22 my.home.ip

then from my home computer (that has sshd installed) i run from terminal: ssh -vv -p 10000 -l user localhost

I always get the following:

OpenSSH_5.3p1 Debian-3ubuntu3, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [::1] port 10000.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host


Is this a limitation that can be overcome by configuring anything on my home computer? or is there anything else I can try?

I've seen a reverse ssh connection made with only plink.exe before, so I know it can be done. Just not sure what is stopping me right now.

EDIT: forgot to mention, I am already forwarding ports 10000 and 22 to my home PC from the home router. I do not have access to my work router until I ask the admin for it.

---

