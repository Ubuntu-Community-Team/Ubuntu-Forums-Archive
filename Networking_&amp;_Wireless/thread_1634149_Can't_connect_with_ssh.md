---
title: "Can't connect with ssh"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by Floven de Sorezé Stockeir on 2010-11-30
Hello,

at the moment I'm trying to set up a simple ssh connection between two computers (running Ubuntu 10.10) on our wireless home network.

On both computers I made sure OpenSSH was installed, server & client side:

```
sudo apt-get install openssh-server openssh-server
```I then disabled both firewalls.

```
sudo ufw disable
```That's all I have done really, but I still can't connect from one pc to the other. I tested 

```
ssh localhost
```which works




So now I try ```
ssh user@hostname
```for which I get: ssh: Could not resolve hostname XXX: Name or service not known

Am I right for using as host- & username what I see when I start a terminal on the server pc?


Please bear with me as I have absolutely very little experience in networking. I read on some places something about the router forwarding port22, but I have no idea what this actually means. I searched for several hours on the internet but didn't find anything which didn't assume prior knowledge of how ports, routers & firewalls work. I really hope someone here can help me.

Thank  you very much,

Floven de Sorezé Stockeir

---

### Post by cavalier911 on 2010-11-30
Try ```
ssh username@i.p.address
```

No connection:

Some tests to run to see if servers running/listening/resolving.

On server machine:

```
sudo netstat -natp | grep sshd
```

Should return:

```
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3957/sshd       
tcp6       0      0 :::22                   :::*                    LISTEN      
```

From client machine:

```
rj@lubuntu:~$ telnet hostname 22
```

Should return:

```
Trying i.p. address of host...
Connected to hostname.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
```

---

### Post by Floven de Sorezé Stockeir on 2010-11-30
Thank you Cavalier911!

I will try right away the I.P. connection.

so I should write:

```
ssh user@ i.p. address
```

I've still got two small questions though:
- USER: should I enter the username from client side or the server's username?
- How do I find the i.p. Address? Is ```
ifconfig
``` "inet addr" good?

Thank you.

---

### Post by Floven de Sorezé Stockeir on 2010-11-30
Well, cavalier's tip worked, thank you cavalier! I managed to connect with ip!


I'm learning step by step :)

---

