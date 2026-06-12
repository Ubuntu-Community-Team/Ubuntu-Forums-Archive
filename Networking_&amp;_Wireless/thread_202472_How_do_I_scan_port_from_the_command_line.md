---
title: "How do I scan port from the command line?"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by xp_newbie on 2006-06-23
I know how to test for open ports on my LAN using the GUI tool in Ubuntu:

System > Administration > Network Tools > Port Scan [tab]

But how do I do that from the command line, **not using GUI**?

Thanks!
Alex

---

### Post by Fass on 2006-06-23
Tried [nmap?](http://www.insecure.org/nmap/)

---

### Post by xp_newbie on 2006-06-23
[QUOTE=Fass]Tried [nmap?](http://www.insecure.org/nmap/)[/QUOTE]

On Fedora Core 4 - yes, I use it.

But on Ubuntu 6.06 I can't find it. :( 

I wonder how the GUI port scanner accomplishes this task without calling under the cover to nmap. :???: 

Thanks!
Alex

---

### Post by Fass on 2006-06-23
[http://packages.ubuntulinux.org/dapper/net/nmap](http://packages.ubuntulinux.org/dapper/net/nmap)

Nmap is in the repositories.

---

### Post by Fac51 on 2006-06-23
yes, check repository....

me likey this...
```
nmap -sS -sV -O -PI -PT <host/IP>
```

---

### Post by xp_newbie on 2006-06-23
Thanks - it is indeed in the repositories, although not installed by default.

Now I am curious as to how the GUI port scanner accomplished this task without calling under the cover to nmap. Any idea?

Thanks,
Alex

---

### Post by corax on 2007-01-08
Hi all,

I did some digging and come up with this :)
(AFAIK netcat (nc) is included in the default install - I checked it :) )

this command does the trick :

```
nc -z -v -w2 IP PORT
```

-z flag is for continue the scan after a port is found (instead of connecting to it).
-v is verbose mode (you cant see the results if don't use this :) )
-w2 is the timeout (2 sec)

(if you write -vv instead of -v the program becomes more verbose it is sometimes useful sometimes not)

example:

```
nc -z -v -w2 127.0.0.1 1-3000
```

scans my (your) computer from port 1 to 3000 (inclusive)

check the netcat manual for more info (```
man netcat
``` or google :) )

bye corax

---

### Post by xp_newbie on 2007-02-25
> **corax said:**
> Hi all,

I did some digging and come up with this :)
(AFAIK netcat (nc) is included in the default install - I checked it :) )

this command does the trick :

```
nc -z -v -w2 <hostname or IP address> <port range>
```

-z flag is for continue the scan after a port is found (instead of connecting to it).
-v is verbose mode (you cant see the results if don't use this :) )
-w2 is the timeout (2 sec)

(if you write -vv instead of -v the program becomes more verbose it is sometimes useful sometimes not)

example:

```
nc -z -v -w2 127.0.0.1 1-3000
```

scans my (your) computer from port 1 to 3000 (inclusive)

check the netcat manual for more info (```
man netcat
``` or google :) )

bye corax

Corax, I just discovered your reply here and I must say: You are king! :)
You have just answered my question of how the GUI does its magic without nmap.

Your 'nc' method works beautifuly!

Thanks,
Alex

---

