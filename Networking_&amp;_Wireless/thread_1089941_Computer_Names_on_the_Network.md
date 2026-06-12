---
title: "Computer Names on the Network"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by guywithcable on 2009-03-07
Hi everyone. I'm trying to figure out why I can't get to my server using its host name.

The ones that are working are running 8.10. I can get to them by using charlotte-desktop.local and hunter-desktop.local. Such as:
```
ssh charlotte@charlotte-desktop.local
```But I can't get to my server at hunter-server.local. That one is running 8.04 Server. It was hunter-server.family (which I also couldn't get to), but I changed /etc/hosts to:

```
127.0.0.1       localhost
192.168.0.10    hunter-server

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```so it would be hunter-server.local. I also can't get to my other computers from it. I get this:

```
hunter@hunter-server:~$ ssh hunter@hunter-desktop.local
ssh: hunter-desktop.local: Name or service not known
```Any ideas?

---

### Post by Iowan on 2009-03-07
Hve you tried just: ```
ssh hunter@hunter-desktop
```

---

### Post by guywithcable on 2009-03-07
> **Iowan said:**
> Hve you tried just: ```
ssh hunter@hunter-desktop
```

I just tried it and got the same result.

```
hunter@hunter-server:~$ ssh hunter@hunter-desktop
ssh: hunter-desktop: Name or service not known
```

---

### Post by Iowan on 2009-03-07
I presume you can ping it by IP address?

---

### Post by guywithcable on 2009-03-07
> **Iowan said:**
> I presume you can ping it by IP address?

Yeah. I can SSH to it by IP address, just not host names. I tried changing the /etc/hosts file again. I'll let you know if that works.

---

### Post by Teknor on 2009-03-08
But you really shouldn't have to edit the hosts file.

Why is it that current Linux distros tend to fail simple local network IP name resolution?  That *other* OS (Windoz) does it well and simple local networks will name resolve easily.

I don't know the answer either (short of editing the hosts file) but in a DHCP network (even simple "at home" networks) the device that serves out the dynamic IP numbers (usually the router) also by default should be doing at least rudimentary name resolution.

I know, this doesn't help.  It's one of my pet peeves with the recent Linux distros.

---

### Post by Iowan on 2009-03-08
[dnsmasq]("http://thekelleys.org.uk/dnsmasq/doc.html") reportedly ties DNS and DHCP together better than DHCP3 that I use. "Someday" I'll get around to trying it.

---

