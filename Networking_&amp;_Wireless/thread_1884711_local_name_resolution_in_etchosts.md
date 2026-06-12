---
title: "local name resolution in /etc/hosts"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by heyneman on 2011-11-21
I'm having some weird issues that I don't understand.  I'm testing some XML-RPC python code locally; starting a server by getting the hostname via commandline 'hostname'.  The weirdness is in what IP this is assigned.  I've been testing by starting the server then looking at the output of netstat -nap to see what IP the server is on.

If my /etc/hosts looks like this (plus some stuff for IPv6 capable hosts below it):

```
127.0.1.1    meka-desktop
10.0.2.15    meka-desktop    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    meka-desktop    localhost6.localdomain6 localhost6
```

then 'meka-desktop' resolves to 127.0.1.1 as expected.

If instead the file looks like

```
10.0.2.15    meka-desktop    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    meka-desktop    localhost6.localdomain6 localhost6
127.0.1.1    meka-desktop
```

(moved the fist line to the bottom) it resolves to 127.0.0.1

Why, if it skips the first line (which actually has meka-desktop as an alias) does it resolve to the localhost line and not make it to the last line?  My assumption would be that it finds the first entry with an alias of 'meka-destop' and returns that IP, but that apparently isn't right.  So what is actually happening?

If it matters, this testing is actually on a VM (the 10.0.2.15 IP is the connection to the host machine's network adapter)

Thanks,

---

