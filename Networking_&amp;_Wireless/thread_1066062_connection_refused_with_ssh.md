---
title: "connection refused with ssh"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by libertarian on 2009-02-10
Good evening all,  I am trying to access my Ubuntu machine at home from a laptop running Ubuntu also.  The computers are on seperate networks and both are behind their respective routers.

When ever I try to executer the ssh command I get a connection refused.

When I am at home and try to access my work computer I get the password prompt for my home machine.

I enabled the firewall on the router I need to get passed to allow incoming ssh connection and outgoing connections.

However this happens:
```

ssh root@xx.xxx.xxx.xxx
ssh: connect to host xxx.xxx.xxx.xxx port 22: Connection refused

```

I also tried to connect as my username on that computer but to no avail.

I tried to follow some guides and I modified the the sshd_config file:
```

LoginGraceTime 120
PermitRootLogin yes

```

I can successfully ping the machine I want to reach.

Any suggestions?  must be surely something simple I missed?

Any help would be much appreciated.

---

### Post by JK3mp on 2009-02-10
Try 
```
sudo ssh -l root xxx.xxx.xxx.xxx -p 22
``` or without the sudo may work too..
-probably didn't need to add this but the xxx's is the  ip address of what your trying to connect to.

---

### Post by libertarian on 2009-02-10
Hi JK3mp,

yes I tried that also.  Apologies for not putting that in teh original post.  It still refuses the connection.

Any other things I might of done wrong?

---

### Post by JK3mp on 2009-02-10
You said you edited the sshd_config file? correct? You could perhaps undo that but im not sure how that would effect your connection. Are your permissions set properly on the comp your trying to connect to?

---

### Post by Neural oD on 2009-02-10
are you sure that the firewall is letting you through - have you port scanned your network - to see if there is a port open for ssh

---

### Post by libertarian on 2009-02-10
> **Neural oD said:**
> are you sure that the firewall is letting you through - have you port scanned your network - to see if there is a port open for ssh

see:
```

sudo netstat -nap | grep :22
tcp6       0      0 :::22                   :::*                    LISTEN  

```

Does that mean is running and on the correct port?

Also how do I scan the router to see if the port is in fact open on my router?

---

### Post by JK3mp on 2009-02-10
Try this.... [http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Remote_Access_using_SSH](http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Remote_Access_using_SSH)  :)

---

### Post by JK3mp on 2009-02-10
If that doesn't help. Or before you even read that give the output of.
```
sudo iptables -L
```

assuming u are using default ubuntu firewall this will check if firewall is blocking it.

Also try 
```
sudo netstat -nap | grep :22
```

to see if your listening on port 22

---

### Post by libertarian on 2009-02-10
Thanks TK3mp I will look at that now.

I was using the Network Tools - Port scan and it has not found any open ports on the destination ip address yet.  Looks like it is a router problem at the other side?

---

### Post by Neural oD on 2009-02-10
> **libertarian said:**
> see:
```

sudo netstat -nap | grep :22
tcp6       0      0 :::22                   :::*                    LISTEN  

```

Does that mean is running and on the correct port?

Also how do I scan the router to see if the port is in fact open on my router?

It would seem so - have u tried nmap from the other side?

---

### Post by libertarian on 2009-02-10
Hi Neural oD

I ran nMap on the destination ip:

PORT     STATE  SERVICE
22/tcp   closed ssh


I will try to open that port again.  Maybe I did it incorrectly on the destination router.  Thanks for all your help.  At leat now I learn't how to verify if the ssh port is open or closed.

Thanks!

---

### Post by JK3mp on 2009-02-10
No problem. And maybe this will help....
[http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Remote_Access_using_SSH](http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Remote_Access_using_SSH)

if you have further problems gettin it going.

---

### Post by Neural oD on 2009-02-10
> **libertarian said:**
> Hi Neural oD

I ran nMap on the destination ip:

PORT     STATE  SERVICE
22/tcp   closed ssh


I will try to open that port again.  Maybe I did it incorrectly on the destination router.  Thanks for all your help.  At leat now I learn't how to verify if the ssh port is open or closed.

Thanks!

Np - glad to be of some assistance :)

---

### Post by libertarian on 2009-02-10
Doing a port scan on the remote machine shows port 22 is open for ssh.

Now when i try to access,  there is no connection refused,  it just hangs.  Any thoughts?

---

### Post by Neural oD on 2009-02-12
you must make sure that ssh is configured correctly - have a look at the docs for ssh - you should be able to come right

---

