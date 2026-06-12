---
title: "Ssh is not working on two machine"
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by sbhavra on 2011-09-09
Hi,
 
I am having two machines having ubuntu installed on it. currently i an not able to connect the machines via ssh and getting connection refused message while connecting to the another machine.
 
I have checked the firewall is enabled. ssh is also installed. When i do the ssh to machine itself it is working. But not for accessing the different machine.
 
Due to this issue i am not able to connect to Mysql server from another machine having mysql client installed on it.
 
Please suggest.
 
Regards,
Suukhbir

---

### Post by Grenage on 2011-09-09
You are 100% sure that openssh-server is installed? (on the machines you are connecting *to*)

---

### Post by sbhavra on 2011-09-09
yup i have checked it. it is installed.
 
Because when i [EMAIL="ssh@machineitself"]ssh@machineitself[/EMAIL]  to itself it is working.

---

### Post by Grenage on 2011-09-09
Interesting; especially if you're not using a firewall.  Are you connecting to the machines by IP or DNS name?

---

### Post by sbhavra on 2011-09-09
I am using the ip address like
ssh [EMAIL="root@172.xx.xx.xxy."]root@172.xx.xx.xxy.[/EMAIL]

---

### Post by Wayne_V on 2011-09-09
first, I would install nmap and make sure the ssh ports are showing open on the other computer.

then,  stop the ssh server and run it in a terminal in debug mode:

$ sudo /etc/init.d/ssh stop
$ sudo /usr/sbin/sshd -vvv

now, when you connect from the other system, if there is a config error it should be obvious in the debug output.

---

### Post by Wayne_V on 2011-09-09
> **sbhavra said:**
> I am using the ip address like
ssh [EMAIL="root@172.xx.xx.xxy."]root@172.xx.xx.xxy.[/EMAIL]

also, with Ubuntu desktop at least (not sure about server), login as root is disabled by default.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Grenage on 2011-09-09
> **sbhavra said:**
> I am using the ip address like
ssh [EMAIL="root@172.xx.xx.xxy."]root@172.xx.xx.xxy.[/EMAIL]

Ok, well in my experience this is usually down to one of three things:

1) ssh-server is not installed
2) sshd is not running
3) firewall

1 and 2 and unlikely in this situation.

Are you positive that you don't have a firewall rule blocking this, either on the server or a device between the client and server?

---

### Post by Vishal Agarwal on 2011-09-09
open the ssh port in firewall. I feel that will be creating problem. Just now i have faced the same problem in one of my local PC.

---

### Post by sbhavra on 2011-09-09
This port is already open in the firewall.

---

### Post by Vishal Agarwal on 2011-09-09
Ok check the opened ports using nmap x.x.x.x
it will show you the opened ports
after that do telnet x.x.x.x
if it telnet then let me know; wil check some other process

Do the same exercise on both of the computers

---

