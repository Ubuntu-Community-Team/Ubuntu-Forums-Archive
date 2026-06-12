---
title: "server dns corrupt cache and how to clear it"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2012-12-04
Hi

Running Ubuntu 12.04 i386 server with Ubuntu-desktop installed (unity-2d).

When I ping my domain I do not get my external ip-address as I should. When others externally ping then they do.

I would like to know how to 


[LIST=1]
[*]Show all the modules options for this server. When It was installed there were a number of options e.g DNS that could be added.
[*]Detect  determine if a service like DNS / BIND9 Postfix etc is running
[*]Stop a service
[*]Remove a service
[*]Clear the DNS cache
[/LIST]
Thanks for your time

---

### Post by Neill_R on 2012-12-04
I still would like to know the howtos but however the cache has cleared now.

---

### Post by papibe on 2012-12-04
Hi Neill_R.
> **Neill_R said:**
> Detect  determine if a service like DNS / BIND9 Postfix etc is running
```
sudo service bind9 status
```
> **Neill_R said:**
> Stop a service
```
sudo service bind9 stop
```
> **Neill_R said:**
> Remove a service
You need to get the package name. In case of bind coincides with the service's name:
```
sudo apt-get remove bind9
```
> **Neill_R said:**
> Clear the DNS cache
You can get rid of the cache only if you are running a service (bind or dnsmasq). The cache is kept only in RAM, so restarting the service should be enough:
```
sudo service bind9 restart
```
Let us know how it goes.
Regards.

---

### Post by Neill_R on 2012-12-04
@freds-server:~$ sudo service bind9 status

[sudo] password: 
bind9: unrecognized service
@freds-server:~$ 

hard to diagnose now since the cache is not corrupt any more.

---

### Post by Neill_R on 2012-12-04
sudo service dnsmasq status
dnsmasq: unrecognized service

---

