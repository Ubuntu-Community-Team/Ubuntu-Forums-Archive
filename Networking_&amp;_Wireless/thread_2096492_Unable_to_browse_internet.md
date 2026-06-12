---
title: "Unable to browse internet"
date: 2012-12-20
forum: Networking &amp; Wireless
---

### Post by vdevanaidu on 2012-12-20
Hi,
 
I am unable to browse internet on my ubuntu 10.04 LTS. Where as I am getting the IP address and able to ping the local router and other machines as well. But unable to ping or browse google.
 
Tried by assigning static IP as well checked resolv.conf everything is fine. No idea what has gone wrong.
 
Any help is highly appreciated.
 
Thank you
Vnaidu

---

### Post by Pjotr123 on 2012-12-20
I advise an upgrade to 12.04 LTS. Version 10.04 will reach end of life in four months, and 12.04 is supported until 2017.

Get 12.04 here:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

This might solve your problem rightaway. Do a clean upgrade:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

Good luck! :)

---

### Post by Grenage on 2012-12-20
> **vdevanaidu said:**
> Hi,
 
I am unable to browse internet on my ubuntu 10.04 LTS. Where as I am getting the IP address and able to ping the local router and other machines as well. But unable to ping or browse google.
 
Tried by assigning static IP as well checked resolv.conf everything is fine. No idea what has gone wrong.
 
Any help is highly appreciated.
 
Thank you
Vnaidu

I assume then, that you can't resolve external names?

```
ping google.com
```

If not, try alternative DNS servers, such as google's:

```
8.8.8.8
8.8.4.4
```

---

### Post by vdevanaidu on 2012-12-20
I tried changing DNS Server address in resolv.conf and tried assigning static IP also. But no use....it was working this morning all of sudden it happned..even I didn't restart the machine in between...don't know what went wrong.

---

### Post by Grenage on 2012-12-20
Given that it *was* working, your internet connection may be down.  If you don't have any other devices to test with, and resetting the router doesn't help, it can't hurt to call your ISP.

---

### Post by vdevanaidu on 2012-12-21
Am able to access internet on other machines. This is the only one machine which is giving trouble.

---

### Post by Grenage on 2012-12-21
In that case, what exactly do you get back when you do the following:

```
traceroute google.com
```

```
ping google.com
```

```
dig google.com
```

```
ping 8.8.8.8
```

Have you tried entering the appropriate settings via the network manager GUI, or is that not an option?

---

