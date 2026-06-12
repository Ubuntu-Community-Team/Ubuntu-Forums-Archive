---
title: "I can't access outside hosts"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by bpont on 2009-02-16
I recently installed ddclient, libio-socket-ssl-perl, and sendmail in order to automate the process of updating my ip address changes to dyndns.org.  I installed everything successfully and configured correctly.

I was logged in remotely from another computer when I did all this.

Afterward, I kept my remote session open and tried to check my e-mail accounts via Evolution.  It could not fetch mail and gave an error about not being able to find the host 'pop.gmail.com'.  I opened a terminal and tried to ping google.com and got 'unknown host'.  I pinged another address and got the same error message.  Obviously, the network is functioning to allow me to be remotely logged in, but I can't seem to access any outside hosts.  I don't know whether or not any of this relates to installing / configuring the aforementioned packages.

Can someone help?

---

### Post by bpont on 2009-02-17
bump

---

### Post by superprash2003 on 2009-02-17
post output of **cat /etc/resolv.conf** and output of **nslookup google.com**

---

### Post by bpont on 2009-02-17
> **superprash2003 said:**
> post output of **cat /etc/resolv.conf** and output of **nslookup google.com**


```
$ cat /etc/resolv.conf
search cable.rcn.com
nameserver 207.172.3.8
nameserver 207.172.3.9
```


```
$ nslookup google.com
Server:         207.172.3.8
Address:        207.172.3.8#53

Non-authoritative answer:
Name:   google.com
Address: 74.125.67.100
Name:   google.com
Address: 74.125.45.100
Name:   google.com
Address: 209.85.171.100
```

---

### Post by jonobr on 2009-02-17
place
74.125.67.100
 or the other address in your browser, does it bring up google?

If not, can you ping those addresses?

same with pop.gmail.com

COuld you try nslookup of that host 
and try and ping it?

---

### Post by bpont on 2009-02-17
> **jonobr said:**
> place
74.125.67.100
 or the other address in your browser, does it bring up google?

If not, can you ping those addresses?

same with pop.gmail.com

COuld you try nslookup of that host 
and try and ping it?

I can ping the IPs of both google.com and pop.gmail.com from nslookup, but I can't ping by hostname:

```
ping: unknown host
```

Is there some kind of configuration issue going on here?

---

### Post by jonobr on 2009-02-17
Check your /etc/resolv.conf file.
Does it have some entry for dns after the hosts entry?

---

### Post by bpont on 2009-02-17
> **jonobr said:**
> Check your /etc/resolv.conf file.
Does it have some entry for dns after the hosts entry?

This is the extent of my /etc/resolv.conf file:

```
$ cat /etc/resolv.conf
search cable.rcn.com
nameserver 207.172.3.8
nameserver 207.172.3.9
```

---

### Post by jonobr on 2009-02-17
eeek... Apolgies...... Should ahve /etc/nsswitch.conf


This defines how hosts are resolved and in which order

---

### Post by bpont on 2009-02-17
> **jonobr said:**
> eeek... Apolgies...... Should ahve /etc/nsswitch.conf


This defines how hosts are resolved and in which order

```
$ sudo cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

### Post by jonobr on 2009-02-17
Modify the line 

```
hosts:          files
```


to say 

```
hosts:          files          dns
```

Test again

---

### Post by superprash2003 on 2009-02-18
also post output of **ifconfig** please..

---

### Post by jonobr on 2009-02-19
Im guessing it worked, or you gave up

---

