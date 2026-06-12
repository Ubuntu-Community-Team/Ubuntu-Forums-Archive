---
title: "How do I turn off a service on a port?"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by josephellengar on 2010-02-03
My school isn't letting me connect to their vpn because I have a service running on port 25.  How do I figure out what service this is and either turn it off or switch it to a different port?
Thank you!

---

### Post by chili555 on 2010-02-03
[http://en.wikipedia.org/wiki/Port_25](http://en.wikipedia.org/wiki/Port_25)

You could always use web-based email, such as Gmail.

---

### Post by josephellengar on 2010-02-03
> **chili555 said:**
> [http://en.wikipedia.org/wiki/Port_25](http://en.wikipedia.org/wiki/Port_25)

You could always use web-based email, such as Gmail.

I do use gmail.  I have no idea what is keeping the port open.

---

### Post by chili555 on 2010-02-03
You have no email client, Evolution, Kmail, etc. set up and configured just in case?

I am not quite sure how to close ports.

---

### Post by josephellengar on 2010-02-03
> **chili555 said:**
> You have no email client, Evolution, Kmail, etc. set up and configured just in case?

I am not quite sure how to close ports.

None.

---

### Post by chili555 on 2010-02-03
Try this, except with port 25, obviously:  [http://tuxarena.blogspot.com/2009/01/tip-of-day-close-port-in-linux.html](http://tuxarena.blogspot.com/2009/01/tip-of-day-close-port-in-linux.html)

---

### Post by DGortze380 on 2010-02-03
please post the output

```

netstat -tulp

```

---

### Post by jflaker on 2010-02-03
Get nmap 
```
sudo apt-get install nmap
```

then run
```
nmap localhost
```

it should tell you what is running on open ports

---

### Post by josephellengar on 2010-02-04
> **DGortze380 said:**
> please post the output

```

netstat -tulp

```

This is the output
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:ipp           *:*                     LISTEN      1933/cupsd      
tcp        0      0 *:smtp                  *:*                     LISTEN      1872/master     



```

---

### Post by josephellengar on 2010-02-04
> **jflaker said:**
> Get nmap 
```
sudo apt-get install nmap
```

then run
```
nmap localhost
```

it should tell you what is running on open ports

Here is the output:
```

Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 998 closed ports
PORT    STATE SERVICE
25/tcp  open  smtp
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.22 seconds

```

---

### Post by josephellengar on 2010-02-04
Strangely enough, even though the above says that smtp is running, in my gufw I have the following rule: 
TO: 25 DENY FROM ANYWHERE

I used the preset rule t block smtp.  I don't understand what is going on.

---

### Post by DGortze380 on 2010-02-04
> **rossholley said:**
> Strangely enough, even though the above says that smtp is running, in my gufw I have the following rule: 
TO: 25 DENY FROM ANYWHERE

I used the preset rule t block smtp.  I don't understand what is going on.

You have SMTP running.

```

tcp 0 0 *:smtp  *:*  LISTEN      1872/master

```

The program is master, I'm not familiar with it. If it's not necessary, try

```

sudo pkill -9 1872

```

A deny rule likely isn't sufficient. It's still clear that a service is running on that port if traffic is denied. You may want to try dropping the traffic, but I think your best solutions is to shut off that service.

---

