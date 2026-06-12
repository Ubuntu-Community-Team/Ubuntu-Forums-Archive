---
title: "How to put dynamic IP address in /etc/hosts"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by Robert Dodier on 2009-09-23
Hello,

I have a netbook (Dell Mini 10v) which is getting a dynamic IP address from a router, either wired or wireless. (Both connections work correctly. Sometimes one is enabled and sometimes the other, sometimes both.)

I wonder if there is a way to put the dynamic IP address (a local address like 192.168.0.xxx) into /etc/hosts. I.e. let's say the name of the netbook is foobar and the assigned IP address is 192.168.0.42. Then I'd like to see a line "192.168.0.42 foobar" in /etc/hosts, and any previous value taken away. (I suppose I could try some ifconfig | awk craziness but I really, really want to steer away from that!)

To back up for a moment, what I really want is for java.net.InetAddress.getAllByName("foobar") to retrieve 192.168.0.42 in addition to 127.0.0.1 (which is the only address returned by InetAddress.getAllByName at present). If you know a way to retrieve 192.168.0.42 without changing /etc/hosts, I would certainly like to hear about it!

I also tried the C library function gethostbyname and it appears to return only what is in /etc/hosts. No surprise there, but since Java's getAllByName is presumably calling gethostbyname, Java can show only what C can.

Thanks in advance to anyone who can shed some light on this problem.

best

Robert Dodier

---

### Post by tkoco on 2009-09-23
Why not *alias* a static IP to the dynamic IP?
Check this tutorial:
[http://ubuntuforums.org/showthread.php?t=1259634](http://ubuntuforums.org/showthread.php?t=1259634)

> **Robert Dodier said:**
> Hello,

I have a netbook (Dell Mini 10v) which is getting a dynamic IP address from a router, either wired or wireless. (Both connections work correctly. Sometimes one is enabled and sometimes the other, sometimes both.)

I wonder if there is a way to put the dynamic IP address (a local address like 192.168.0.xxx) into /etc/hosts. I.e. let's say the name of the netbook is foobar and the assigned IP address is 192.168.0.42. Then I'd like to see a line "192.168.0.42 foobar" in /etc/hosts, and any previous value taken away. (I suppose I could try some ifconfig | awk craziness but I really, really want to steer away from that!)

To back up for a moment, what I really want is for java.net.InetAddress.getAllByName("foobar") to retrieve 192.168.0.42 in addition to 127.0.0.1 (which is the only address returned by InetAddress.getAllByName at present). If you know a way to retrieve 192.168.0.42 without changing /etc/hosts, I would certainly like to hear about it!

I also tried the C library function gethostbyname and it appears to return only what is in /etc/hosts. No surprise there, but since Java's getAllByName is presumably calling gethostbyname, Java can show only what C can.

Thanks in advance to anyone who can shed some light on this problem.

best

Robert Dodier

---

### Post by capscrew on 2009-09-24
> **Robert Dodier said:**
> ...
I wonder if there is a way to put the dynamic IP address (a local address like 192.168.0.xxx) into /etc/hosts...
The /etc/hosts file is for the static mapping of the network IP addresses to a hostnames.  In was never designed for dynamic mapping.> 

To back up for a moment, what I really want is for java.net.InetAddress.getAllByName("foobar") to retrieve 192.168.0.42 in addition to 127.0.0.1 (which is the only address returned by InetAddress.getAllByName at present). If you know a way to retrieve 192.168.0.42 without changing /etc/hosts, I would certainly like to hear about it!

I also tried the C library function gethostbyname and it appears to return only what is in /etc/hosts. No surprise there, but since Java's getAllByName is presumably calling gethostbyname, Java can show only what C can...


Local dynamic DNS can be handled by DNSMasq or Bind9.  For simple networks I would recommend [**_DNSMasq_**]("http://www.thekelleys.org.uk/dnsmasq/doc.html").  You should be able to retrieve the hostname with the "hostname" variable. See ```
man hostname
```

---

### Post by Robert Dodier on 2009-09-24
> **capscrew said:**
> The /etc/hosts file is for the static mapping of the network IP addresses to a hostnames.  In was never designed for dynamic mapping.

Let's ignore /etc/hosts then. There is a dynamic IP address assigned to the netbook. How can I find that address, short of grepping the output of ifconfig ?

Perhaps more to the point, how does ifconfig determine the address? Presumably it's a C library function somewhere. I guess if all else fails, I'll try to find the source code, but perhaps someone in this forum knows already.

> **capscrew said:**
> Local dynamic DNS can be handled by DNSMasq or Bind9.  For simple networks I would recommend [**_DNSMasq_**]("http://www.thekelleys.org.uk/dnsmasq/doc.html").  You should be able to retrieve the hostname with the "hostname" variable.

Thanks, but I don't want name resolution.

All the best, Robert Dodier

---

