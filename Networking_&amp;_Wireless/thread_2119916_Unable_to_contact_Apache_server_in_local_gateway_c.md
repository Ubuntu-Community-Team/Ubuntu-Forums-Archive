---
title: "Unable to contact Apache server in local gateway computer"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by baskar007 on 2013-02-25
Hi all,
I have two kubuntu PC's connected via lan (12.04 and 11.04). I have apache installed in 12.04 PC and its working fine on localhost.

I did a lan setup to use 12.04 as a gateway for 11.04 so i can share my mobile broadband over lan.

Now internet sharing is working fine. 

but I cant view 12.04 PC's webpage... if I enter 12.04 IP address in 11.04 web brwoser it gives me an error request timeout!..

I not well in networking ... Is there is any way to fix it?? 

Thanks in advance

---

### Post by fdrake on 2013-02-25
in the 11.04 type:
```

route

```
the gateway should be the ip address of 12.04 from pc 11.04

---

### Post by baskar007 on 2013-02-25
> **fdrake said:**
> in the 11.04 type:
```

route

```
the gateway should be the ip address of 12.04 from pc 11.04

Here is the output:

```
baskar@baskar-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     1      0        0 eth0
default         169.254.43.84   0.0.0.0         UG    0      0        0 eth0
baskar@baskar-desktop:~$ 
```

12.04 ip address  169.254.43.84 is correct

---

### Post by fdrake on 2013-02-25
```
less /etc/apache2/sites-enabled/000-default 
```
also nmap may help too , checking if you have port 80 closed
```

nmap -p 80 169.254.43.84

```

also try to stop the bridge service and try to connect to the server, are you abel to connect like that. Your bridge configuration may creat problem to the apache server(port 80). If that is the problem, you could switch the position. make the other computer the bridge and attach the webserver to it.

---

### Post by baskar007 on 2013-02-26
Thanks fdrake.
Here is the output of nmap -p 80 169.254.43.84

```

baskar@baskar-desktop:~$ nmap -p 80 169.254.43.84

Starting Nmap 5.21 ( http://nmap.org ) at 2002-01-01 05:02 IST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.13 seconds

```


As nmap suggest (with PN argument)


```
baskar@baskar-desktop:~$ **nmap -p 80 169.254.43.84 -PN**

Starting Nmap 5.21 ( http://nmap.org ) at 2002-01-01 05:03 IST
Nmap scan report for 169.254.43.84
Host is up.
PORT   STATE    SERVICE
80/tcp filtered http

Nmap done: 1 IP address (1 host up) scanned in 2.44 seconds
baskar@baskar-desktop:~$ 
```

---

### Post by baskar007 on 2013-02-26
OK. Finally I got it. :o
Just added 11.04 IP to "Allow connections from host" policy in firestrater firewall application. Now my web server working fine... :D

> **baskar007 said:**
> Thanks fdrake.
Here is the output of nmap -p 80 169.254.43.84

```

baskar@baskar-desktop:~$ nmap -p 80 169.254.43.84

Starting Nmap 5.21 ( http://nmap.org ) at 2002-01-01 05:02 IST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.13 seconds

```


As nmap suggest (with PN argument)


```
baskar@baskar-desktop:~$ **nmap -p 80 169.254.43.84 -PN**

Starting Nmap 5.21 ( http://nmap.org ) at 2002-01-01 05:03 IST
Nmap scan report for 169.254.43.84
Host is up.
PORT   STATE    SERVICE
80/tcp filtered http

Nmap done: 1 IP address (1 host up) scanned in 2.44 seconds
baskar@baskar-desktop:~$ 
```

---

### Post by fdrake on 2013-02-26
> **baskar007 said:**
> OK. Finally I got it. :o
Just added 11.04 IP to "Allow connections from host" policy in firestrater firewall application. Now my web server working fine... :D

i could not reply earlier but I am glas you were able to cong the firewall.

---

