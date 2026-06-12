---
title: "Can't ping beyond bridge to qemu and router"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by hvn on 2011-07-18
Hi,

Using v. 10.04, I've created the bridge br0 to be able to access the virtual machine running on qemu. However, since its creation I find I'm unable to ping beyond my router. Other machines in the LAN can be reached fine. The other way around, e.g. ssh to the Ubuntu machine, doesn't work: connection refused.
My intention is to be able to use VNC (remote desktop access) to the Ubuntu machine. Locally it works fine, but from the other side of the router there's no access. Despite that I've added port 5900 to my NAT table and VNC server running. Any idea on how to solve this ?

Thank you.

---

### Post by jmoorse on 2011-07-18
Just to clarify: you cannot ping beyond your gateway from the 'server'?  

Please post this output from the server

```

route -n

```

---

### Post by hvn on 2011-07-18
> **jmoorse said:**
> Just to clarify: you cannot ping beyond your gateway from the 'server'?  


Correct

> **jmoorse said:**
> 
Please post this output from the server

```

route -n

```

Please see attachment. If I post in here, all formatting gets lost.

---

### Post by jmoorse on 2011-07-18
You gateway metric for br0 is 1000, 0 for eth0.  That is likely your problem.

Please run:

```

sudo route del default gw 10.0.0.138 dev eth0

```

And see if that fixes the problem.  If it breaks anything the following will re-add is:

```

sudo route add default gw 10.0.0.138 dev eth0

```

---

### Post by hvn on 2011-07-18
> **jmoorse said:**
> You gateway metric for br0 is 1000, 0 for eth0.  That is likely your problem.

Please run:

```

sudo route del default gw 10.0.0.138 dev eth0
```This does fix the problem.

> **jmoorse said:**
> And see if that fixes the problem.  If it breaks anything the following will re-add is:

```

sudo route add default gw 10.0.0.138 dev eth0

```

Thank you very much.

---

