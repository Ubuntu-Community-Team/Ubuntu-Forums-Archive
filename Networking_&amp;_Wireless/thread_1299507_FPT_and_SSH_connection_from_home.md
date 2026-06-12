---
title: "FPT and SSH connection from home"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by nylee on 2009-10-24
Dear Ubuntu Uers:
 
I'd like to ask network related problems. 
 
1) I have 'Server' at remote place. In most case, that Server works fine. 
But, once 'Server' is rebooted, I cannot ftp/ssh-connect to 'Server' from home, but I can ftp/ssh-connect to 'Server' from computers which are under the same GATEWAY. 
 
To solve this problem, I re-activated lan card even though that lan card was already activated and usable(since I am able to connect 'Server' from computers that are under the same GATEWAY, I know that lan card is OK). This solution is not good since it is not usable at home. 
 
I'd like to know how this happens and how I solve this problem. 
 
2) Sometimes, I can ssh-connect to 'Server', but I cannot ftp-connect to 'Server' from home. Since I could ssh-connect to 'Server', I restarted vsftp daemon by '/etc/init.d/vsftpd restart'. Then 'Server' is ftp-connectable from computers that are under the same GATEWAY, but not from home.
 
I'd like to ask you how to solve this problem.
 
Thanks in advance
 
nylee

---

### Post by tzicatl on 2009-10-24
Do you have some kind of firewall activated?

```
iptables --list 
```

might tell you.

---

### Post by nylee on 2009-10-24
I did 
 
/sbin/iptables --list
 
it shows 
 
Chain FORWARD (policy ACCEPT)
target      prot opt source       destination
 
Chain INPUT (policy ACCEPT)
target      prot opt source       destination
 
Chain OUTPUT (policy ACCEPT)
target      prot opt source       destination
 
 
I am not familar with linux commands. I don't know what above means. 
The most annoying problem to me is that the server has been ssh/ftp-connectable for a long time. But two days ago I uploaded large data(3.5GB), and ftp daemon seemed to be dead. So I rebooted Server. After that, I cannot ftp-connect to Server from home, but I can ftp-connect to Server from other computers that are under same Gateway number. 
 
Thanks 
 
nylee

---

### Post by tzicatl on 2009-10-24
> I did 
 
/sbin/iptables --list
 
it shows 
 
Chain FORWARD (policy ACCEPT)
target      prot opt source       destination
 
Chain INPUT (policy ACCEPT)
target      prot opt source       destination
 
Chain OUTPUT (policy ACCEPT)
target      prot opt source       destination

 
 That means that there are no rules for the firewall. You can read that as "Firewall disabled".

If that is in your server then now you can be shure that it is not a firewall problem and move on.




> I am not familar with linux commands. I don't know what above means. 
The most annoying problem to me is that the server has been ssh/ftp-connectable for a long time. But two days ago I uploaded large data(3.5GB), and ftp daemon seemed to be dead. So I rebooted Server. After that, I cannot ftp-connect to Server from home, but I can ftp-connect to Server from other computers that are under same Gateway number. 
 
Thanks 
 
nylee


Can you ping you ftp server from home?
Now sounds like a network/routing problem.

Noe

---

### Post by lensman3 on 2009-10-24
Are you sure that "/etc/init.d/vsftpd" is starting at boot?  Reboot your machine and from a text window do "ps ax | grep vsftpd".  You should have two lines with vsftpd in them, one the "grep" and the second the "real" daemon.

Also does your network connection automatically start after a reboot?  Mine doesn't until I try to go out the first time.  After that the connection is maintained.

Have you tried using the free "Filezilla" to login?  It has a sftp client that will connect via Openssh, which is a secure ftp.  Filezilla also has the typical ftp clients too.

---

### Post by nylee on 2009-10-25
Thanks for your replies.
 
Let me say the situation again. I have follwoing computes.
 
Server: located at workplace, and has two lan cards. One lan card is connected to 'Router'(let's call its fixed ip = IP_1), and the other lan card has its own fixed ip = IP_2. 
 
Office PC 1: connected to 'Router'
 
Office PC 2: has its own fixe ip = IP_3, but it has the same GATEWAY number with 'Server' and 'Router'. 
 
Home PC: has dynamic ip, and does not have the same GATEWAY number with 'Server'
 
1) When Server is rebooted, the ssh/ftp-connection (Server - Office PC 1) is OK. 
It is also OK for (Server - Office PC 2), in such case I had to use IP_2 and IP_3 for the connection (Server - Office PC 2). But, ssh/ftp-connection (Server - Home PC) is not OK. To make it possible, I re-activate the lan card one more time. 
 
What I wonder is why ssh/ftp connection between computers under the same GATEWAY is OK, but not for Home PC.
 
2) The method which I did for the above problem is not, but at least it works. The current problem is why I cannot have ftp-connection between 'Server' and 'Home PC'. 
This connection has been OK for long time. All other ssh/ftp-connections, including ssh-connection between 'Server' and 'Home PC', are OK. 
 
I had not changed any setting in vsftpd. The ftp has been OK up to yesterday, but not OK today. I don't how such phenonmenon is possible. 
 
Again, thank you.
 
nylee

---

