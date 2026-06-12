---
title: "What is this IP?"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by GolemdX on 2010-03-17
If somebody can find a better place to ask this, please tell me. I couldn't think of anything else.

Back in November I had a problem, which included an error like this:
```
apache2: Could not reliably determine the server's fully qualified domain name, using 8.15.7.103 for ServerName
Syntax OK
```
Now, that problem is completely solved, but another one has risen.

I was setting up a java application, and got an error. "Unable to Connect to 8.15.7.103.". I didn't want it to connect to that IP, I wanted it to connect to localhost. I have a dynamic IP that doesn't last that long, and according to the internet, that IP is somewhere in the US (I live in Canada)!

What could be causing this IP to be tied to my computer/localhost? Thanks.

---

### Post by beanhead on 2010-03-17
Dynamic ip changes and is not always update very well. I hope your using a paid version. The free dyn dns is full of problems.
I think bluehost is the way to go :D
Ron

---

### Post by GolemdX on 2010-03-18
I'm actually using ZoneEdit for my dynamic IP changes. Plus, I switched 'Dynamic DNS' providers between November and now.

I don't really think that's related, because in the configuration files for the application I'm trying to set up... it's set to try to connect to localhost, yet it comes up with a 'connection refused to 8.15.7.103'.

---

### Post by DGortze380 on 2010-03-18
> **GolemdX said:**
> I'm actually using ZoneEdit for my dynamic IP changes. Plus, I switched 'Dynamic DNS' providers between November and now.

I don't really think that's related, because in the configuration files for the application I'm trying to set up... it's set to try to connect to localhost, yet it comes up with a 'connection refused to 8.15.7.103'.

output please

```

cat /etc/hosts

cat /etc/resolv.conf

```

---

### Post by GolemdX on 2010-03-18
```
golemdx@dobe-server:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       dobeserver

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

```
golemdx@dobe-server:~$ cat /etc/resolv.conf
domain My
search My Foo
nameserver 192.168.2.1
```

EDIT: If it makes a difference, this is the topic where I first encountered this IP: [http://ubuntuforums.org/showthread.php?t=1326949](http://ubuntuforums.org/showthread.php?t=1326949)

---

### Post by GolemdX on 2010-03-19
Does anybody know of another place to ask about this?

---

