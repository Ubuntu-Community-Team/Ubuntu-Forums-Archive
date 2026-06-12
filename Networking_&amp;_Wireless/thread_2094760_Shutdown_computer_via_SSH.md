---
title: "Shutdown computer via SSH?"
date: 2012-12-14
forum: Networking &amp; Wireless
---

### Post by PDA1 on 2012-12-14
I've figured out how to connect to various of my computers on my home LAN so I can stream music, video and transfer files around to the various computers.

Let's say the computer I principally work from is called "A".

Further, the computer I connect to is called "B".

Since I'm lazy, is there a way to shut down computer "B" from computer "A"?

---

### Post by DoktorSeven on 2012-12-14
Sure:

[b]ssh -l user computerb

sudo shutdown -h now[/b]

Of course, the user you log into must be able to issue sudo commands.

---

### Post by haqking on 2012-12-14
> **PDA1 said:**
> I've figured out how to connect to various of my computers on my home LAN so I can stream music, video and transfer files around to the various computers.

Let's say the computer I principally work from is called "A".

Further, the computer I connect to is called "B".

Since I'm lazy, is there a way to shut down computer "B" from computer "A"?

```
ssh user@remote_computer 
```

```
sudo poweroff
``` or

```
ssh user@remote_computer 
```

```
sudo shutdown -h now
```

---

### Post by PDA1 on 2012-12-14
Thanks but that's pretty confusing.

Let's say the user on B is Chris

The IP of Chris is 192.154.1.8

How would I issue the command given the syntax you provided below?

---

### Post by PDA1 on 2012-12-14
The reply I got was;

sudo: no tty present and no askpass program specified

---

### Post by haqking on 2012-12-14
> **PDA1 said:**
> Thanks but that's pretty confusing.

Let's say the user on B is Chris

The IP of Chris is 192.154.1.8

How would I issue the command given the syntax you provided below?

how is it confusing ?

[COLOR=#660000]ssh user@192.154.1.8 

sudo poweroff[/COLOR]

user is the user with SSH access and sudo rights

---

### Post by PDA1 on 2012-12-14
It doesn't work.

I tried it.

Like this 

ssh Frank@192.142.1.89 sudo poweroff

Then I'm asked for the password of Frank.

I enter the password.

The reply I get is;

sudo: no tty present and no askpass program specified

---

### Post by Doug S on 2012-12-14
I mostly shutdown and/or re-boot my computers via ssh. haqking's method doesn't work for me either. Why? I'm guessing because there is no way to supply the sudo password.
Just login via ssh and then issue the command, basically what DoktorSeven said. Example:```
doug@doug-64:~/tcpdump/054$ [COLOR=red]ssh [/COLOR][COLOR=red]doug@s16[/COLOR]
doug@s16's password:
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-34-generic-pae i686)
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
  System information as of Fri Dec 14 14:15:34 PST 2012
  System load:  0.0              Processes:           67
  Usage of /:   7.7% of 1.79TB   Users logged in:     1
  Memory usage: 38%              IP address for eth0: 192.168.111.113
  Swap usage:   0%
  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
0 packages can be updated.
0 updates are security updates.
Last login: Sun Dec  9 16:43:04 2012 from doug-xps2.smythies.com
doug@s16:~$ [COLOR=red]sudo shutdown -h now[/COLOR]
[sudo] password for doug:
doug@s16:~$
Broadcast message from doug@s16
        (/dev/pts/1) at 14:15 ...
The system is going down for halt NOW!
Connection to s16 closed by remote host.
Connection to s16 closed.

```

---

### Post by haqking on 2012-12-14
> **Doug S said:**
> I mostly shutdown and/or re-boot my computers via ssh. haqking's method doesn't work for me either. Why? I'm guessing because there is no way to supply the sudo password.
Just login via ssh and then issue the command, basically what DoktorSeven said. Example:```
doug@doug-64:~/tcpdump/054$ [COLOR=red]ssh [/COLOR][COLOR=red]doug@s16[/COLOR]
doug@s16's password:
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-34-generic-pae i686)
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
  System information as of Fri Dec 14 14:15:34 PST 2012
  System load:  0.0              Processes:           67
  Usage of /:   7.7% of 1.79TB   Users logged in:     1
  Memory usage: 38%              IP address for eth0: 192.168.111.113
  Swap usage:   0%
  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
0 packages can be updated.
0 updates are security updates.
Last login: Sun Dec  9 16:43:04 2012 from doug-xps2.smythies.com
doug@s16:~$ [COLOR=red]sudo shutdown -h now[/COLOR]
[sudo] password for doug:
doug@s16:~$
Broadcast message from doug@s16
        (/dev/pts/1) at 14:15 ...
The system is going down for halt NOW!
Connection to s16 closed by remote host.
Connection to s16 closed.

```


it was my fault, i shouldnt of displayed it as all one command, I assumed the OP would realise i meant ssh in then issue the ssh command, however that being said, it works as one command for me on my box here, it asks for sudo password.

but as i said i meant it seperately, i have edited

---

### Post by PDA1 on 2012-12-14
Fantastic!

It works perfectly!

Thank you!

---

