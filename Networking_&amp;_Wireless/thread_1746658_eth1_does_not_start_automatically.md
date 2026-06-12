---
title: "eth1 does not start automatically"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by praguer on 2011-05-02
Hello.  I have static eth1 defined. When I boot or restart, the networking will not start automatically - i must do it from terminal by ifup eth1.

Where can I put this command to have it autostart?

---

### Post by wojox on 2011-05-02
You need to go into Network Connections and edit your eth1. There will be a bx to check that says "start automatically".

---

### Post by praguer on 2011-05-02
I have done this before I posted.

---

### Post by wojox on 2011-05-02
> **praguer said:**
> I have done this before I posted.

And the box t the bottom that says "For all users?"

---

### Post by praguer on 2011-05-02
[IMG]http://iplaq.com/public/Ubuntu2_%5BRunning%5D-20110502-080936.png[/IMG]> **wojox said:**
> And the box t the bottom that says "For all users?"

---

### Post by praguer on 2011-05-02
I upgraded to 11.4 and it now works.

---

### Post by granaet on 2011-12-15
Hi

Here the same. 
Is there a way to start eth1 from the commandpromt? I have ubuntu 11.10 server with no desktop.

greetz
Granaet
the Netherlands

---

### Post by praguer on 2011-12-15
> **granaet said:**
> Hi

Here the same. 
Is there a way to start eth1 from the commandpromt? I have ubuntu 11.10 server with no desktop.

greetz
Granaet
the Netherlands

ifup eth1

---

### Post by granaet on 2011-12-16
Hi

```
ifup eth1
```
works fine

but

when I reboot the machine eth1 again is not activated

is there a way to activate eth1 automatically?

by the way
my knowledge of linux/ubuntu is almost zero

greetz
Granaet
the Netherlands

---

### Post by praguer on 2011-12-16
> **granaet said:**
> Hi

```
ifup eth1
```
works fine

but

when I reboot the machine eth1 again is not activated

is there a way to activate eth1 automatically?

by the way
my knowledge of linux/ubuntu is almost zero

greetz
Granaet
the Netherlands

You could stick it at the end of /etc/init.d/rc - you need to do it as root.

---

### Post by sabakarunner on 2012-08-21
Add 

```
auto eth1
```

to the /etc/network/interfaces file.

---

