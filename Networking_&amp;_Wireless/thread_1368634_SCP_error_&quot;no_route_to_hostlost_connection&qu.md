---
title: "SCP error &quot;no route to host/lost connection&quot;"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by egar12 on 2009-12-30
When I attempt to scp from the host (Ubuntu) to the remote server I receive "no route to host/lost connection" ..I've started ssh on the host(Ubuntu) and can ssh fine between the host and the remote computer (and vice-versa) (I can ping as well). The remote computer is a vm (virtualbox).. Any ideas?

Thank you in advance.

---

### Post by Grim76 on 2009-12-30
Are you using the following format for scp:

$scp <file> <username>@<host name or IP>:/remote/file/location

---

### Post by egar12 on 2009-12-31
Thanks for the note. I'm using:

scp -r -v /desktop/(folder)/(file folder) [email]root@(remotehost.com[/email]):/tmp/

debug1: Applying options for *
debug1: Connecting to (remotehost.com) [192.168.56.102] port 22.
debug1: connect to address 192.168.56.102 port 22: No route to host
ssh: connect to host (remotehost.com) port 22: No route to host
lost connection

---

### Post by shairozan on 2009-12-31
Let's see what your network looks like, because it's possible there is no default route established. 

First, post the output of the following:

```
ifconfig
```

Then post the output of the following:

```
ip route
```

We know DNS is working because it's resolving an address, but it looks like it doesn't have a route there. Are you using a router as a DHCP Server?

---

