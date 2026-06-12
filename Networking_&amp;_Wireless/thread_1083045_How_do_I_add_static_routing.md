---
title: "How do I add static routing?"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by champi0n on 2009-02-28
I cannot seem to add any static routing rules and get them to work.

In the command line if i do something like :
```

sudo route add -host 82.44.142.92 eth0
sudo route add default gw 82.44.142.92

```

My networking will work, but I need to have those 2 routes added on startup (which I can't seem to accomplish)

---

### Post by capscrew on 2009-02-28
> **champi0n said:**
> I cannot seem to add any static routing rules and get them to work.

In the command line if i do something like :
```

sudo route add -host 82.44.142.92 eth0
sudo route add default gw 82.44.142.92

```

My networking will work, but I need to have those 2 routes added on startup (which I can't seem to accomplish)

See here: [http://ubuntuforums.org/archive/index.php/t-234207.html]("http://ubuntuforums.org/archive/index.php/t-234207.html")

There are 2 techniques discussed in the post.

---

### Post by champi0n on 2009-02-28
neither of those solutions are working.

/etc/network/interfaces
```

up /sbin/route add -host 82.44.142.92 eth0
up /sbin/route add default gw 82.44.142.92

```

Fails to bring up eth0
SIOCADDRT: No such process

/etc/network/if-up.d/static-routes
```

#!/bin/sh
# Set static routes
#
/sbin/route add -host 82.44.142.92 eth0
/sbin/route add default gw 82.44.142.92

```
chmod 777 static-routes

Fails to bring up eth0
SIOCADDRT: No such process

From the command line
```

sudo route add -host 82.44.142.92 eth0
sudo route add default gw 82.44.142.92

```
Everything works great.

---

### Post by champi0n on 2009-02-28
I think it may lie in the problem that it cannot bring up eth0 unless those routes are added? (The gateway ip is on a different block then the static ip)

where can i add a file that adds the routes before bringing up eth0?

---

### Post by capscrew on 2009-02-28
I believe that the method may have changed or that info was not exactly correct.

You have some interesting problems to overcome.  Who knows waht is affecting what.  By my way  of thinking the "route add" command is for the kernel to process.  The interface uses it.  The reason for adding it to the interfaces file allows routes to be added on an interface basis.

Here is the same idea but slightly different syntax:
[http://www.linuxreport.org/content/view/33/25/]("http://www.linuxreport.org/content/view/33/25/")

If you will permit me asking, why is the GW not on the same subnet as the host.  To my way of thinking the GW means just that -- the nearside interface of the local router ie: the gateway out of the subnet.  When using this notion I just add "gateway xxx.xxx.xxx.xxx" to the interfaces file.

---

### Post by champi0n on 2009-02-28
> **capscrew said:**
> I believe that the method may have changed or that info was not exactly correct.

You have some interesting problems to overcome.  Who knows waht is affecting what.  By my way  of thinking the "route add" command is for the kernel to process.  The interface uses it.  The reason for adding it to the interfaces file allows routes to be added on an interface basis.

Here is the same idea but slightly different syntax:
[http://www.linuxreport.org/content/view/33/25/]("http://www.linuxreport.org/content/view/33/25/")

If you will permit me asking, why is the GW not on the same subnet as the host.  To my way of thinking the GW means just that -- the nearside interface of the local router ie: the gateway out of the subnet.  When using this notion I just add "gateway xxx.xxx.xxx.xxx" to the interfaces file.

I've typically never come across the gateway being on a different subnet before, but the server is co-located and that's how they manage their network i guess. I got an ip block of XX ip's and the gateway is different then the ip's i got.

Maybe i'll add that as a startup script to execute after/during boot? rather then trying to tie it directly to the interface?

---

### Post by capscrew on 2009-02-28
I'd talk to the co-lo.   Misconfiguration is always a possibility.  I saw it all the time in the datacenter I worked at.  Asking definitely in order here.  Why beat your head against a wall to overcome their mistake.

---

