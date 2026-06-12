---
title: "Ubuntu server won't connect to Interne (wired network)"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by nautica17 on 2010-06-10
Okay, so I just installed Ubuntu server edition on to an old Dell desktop. The only problem is that I can't get the Internet to work. 

I have tried the following and I guess it doesn't work: 

```

sudo ifconfig eth0 192.168.1.52/24 up

sudo route add default gw 192.168.1.1

```Each of those commands don't give me any error and it would seem like everything works fine, until I try to ping google or any website and I get an error that tells me that no host was found. 

I was hoping someone could steer me in the right direction. I'm fairly new to Linux and trying to learn this stuff. 

Edit: I am using version 10.04 of Ubuntu server.

---

### Post by chili555 on 2010-06-10
> sudo ifconfig eth0 192.168.1.52/24 up

I think this ought to be:```
sudo ifconfig eth0 192.168.1.52 up
```Can you ping the router?```
ping -c3 192.168.1.1
```Have you added nameservers to /etc/resolv.conf?```
sudo su
echo "nameserver 192.168.1.1" > /etc/resolv.conf
exit
```

---

### Post by Iowan on 2010-06-10
Verify those commands with **ifconfig -a** and **route -n**
**chili555** sneaked in under me ;) so I thought I better see if I was being redundant...

---

### Post by nautica17 on 2010-06-10
> **chili555 said:**
> I think this ought to be:```
sudo ifconfig eth0 192.168.1.52 up
```Can you ping the router?```
ping -c3 192.168.1.1
```Have you added nameservers to /etc/resolv.conf?```
sudo su
echo "nameserver 192.168.1.1" > /etc/resolv.conf
exit
```

Okay I fixed the first line and it worked. Pinging my own ip works. But pinging websites doesn't. The second line I originally used now gives me a message like this: "SIOCADDRT: File exists".

Edit: I'm not sure what to do now. I also tried the nameserver stuff and I guess it worked, I didn't get any errors or anything like that.

---

### Post by nautica17 on 2010-06-10
> **Iowan said:**
> Verify those commands with **ifconfig -a** and **route -n**
**chili555** sneaked in under me ;) so I thought I better see if I was being redundant...

Okay, I just tried those two and from the info I get I don't see anything disabled, so it seems like everything should be fine with the set up overall.

---

### Post by Iowan on 2010-06-10
Status check:

**ifconfig -a** shows eth0 with IP address 192.168.1.52?
**route -n** (bottom line) shows gateway (UG) as 192.168.1.1?
**cat /etc/resolv.conf** shows (among other things) "nameserver 192.168.1.1"?
You can successfully **ping 192.168.1.1**?

---

### Post by nautica17 on 2010-06-10
> **Iowan said:**
> Status check:

**ifconfig -a** shows eth0 with IP address 192.168.1.52?
**route -n** (bottom line) shows gateway (UG) as 192.168.1.1?
**cat /etc/resolv.conf** shows (among other things) "nameserver 192.168.1.1"?
You can successfully **ping 192.168.1.1**?

Yes to all 4 questions. And I just got it working. Turns out I put an extra e when I was typing "resolv". 

Thank-you so much (to both you guys)! I pinged google.com and it started returning packets. :)

---

### Post by Iowan on 2010-06-10
Give it a day or so to make sure it _stays_ fixed, then mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)
Congrats!

---

