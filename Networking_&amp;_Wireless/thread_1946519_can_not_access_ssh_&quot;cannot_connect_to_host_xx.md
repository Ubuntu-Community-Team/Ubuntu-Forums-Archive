---
title: "can not access ssh &quot;cannot connect to host xx.xx.xx.x port 22 : connection refused&quot;"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by Billcarey4 on 2012-03-25
Can not access ssh from a remote desktop or from my own.

```

ssh william-desktop@xx.xx.xx.x
ssh: connect to host xx.xx.xx.x port 22: Connection refused

```ssh_config and sshd_config both are configured correctly.
```

william@william-desktop:~$ ssh localhost
william@localhost's password: 
Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-16-generic-pae i686)

 * Documentation:  https://help.ubuntu.com/

Last login: Sat Mar 24 22:04:14 2012 from localhost

william@william-desktop:~$ ps -A | grep sshd
 5087 ?        00:00:00 sshd
william@william-desktop:~$ 

```attempts to log in under localhost are successful as you can see. Any attempt to access from any other computer has failed.

Googled all day about the topic with no working results.

any help will be much appreciated

---

### Post by Jest3r on 2012-03-25
Hello,

 You might want to check if sshd is listening for remote connections as well as loopback connections.

You should see something like the below if the sshd process is listening for remote connections
```
 $ netstat -ln --tcp -v4 | grep 22
 tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN  

```
If you see something like the below, then there might be a problem with /etc/ssh/sshd_config
```
 $ netstat -ln --tcp -v4 | grep 22
 tcp   0    0   127.0.0.1:22                 0.0.0.0:*        LISTEN       
```


You might want to check the *ListenAddress* in /etc/ssh/sshd_config to make sure it dosn't have a loopback interface ( 127.0.0.1 ) listed as the *ListenAddress*

Hope it helps

---

### Post by Billcarey4 on 2012-03-25
cmd output
```

william@william-desktop:~$ netstat -ln --tcp -v4 | grep 22
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN 

```

---

### Post by Billcarey4 on 2012-03-25
seams as though there is something else wrong.

---

### Post by madverb on 2012-03-25
Why are you doing:
```
ssh william-desktop@xx.xx.xx.x
```
When you should be doing:
```
ssh william@xxx.xxx.xxx.xxx
```
???

---

### Post by Billcarey4 on 2012-03-25
in the start of my venture earlier today.
 ```
william@william-desktop:~$ ssh william@75.70.59.7
ssh: connect to host 75.70.59.7 port 22: Connection refused

```

when i started this thread i was a bit tired. i clearly made a big mistake.

---

### Post by codemaniac on 2012-03-25
The ssh commandline should be```
ssh user@hostIP
```
In your case ```
ssh william@xxx.xxx.xxx.xxx
```

---

### Post by madverb on 2012-03-25
Are you trying to connect to it remotely or over the local network? Why are you putting in a public IP?

---

### Post by agillator on 2012-03-25
Have you checked to make sure the william-desktop machine's firewall is not blocking port 22?

---

### Post by Billcarey4 on 2012-03-25
This is the problem.I appreciate the help.

---

### Post by Billcarey4 on 2012-03-25
How can i find the host ip?

---

### Post by agillator on 2012-03-25
On the machine you need the ip address for, open a terminal and type ifconfig. From elsewhere on the LAN you can try, if nmap is installed, nmap -sP <network CIDR>, for example nmap -sP 192.168.1.0/24. If the machine responds to pings it will be listed if you can identify it either by its name or by means of elimination. Or, do you have access to the DHCP server and can you get it that way?

---

### Post by Billcarey4 on 2012-03-25
problem solved. Thank you for the help. it was truly enlightening.

---

