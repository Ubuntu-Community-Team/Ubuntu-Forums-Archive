---
title: "Routing problem with virtual machine"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by hroitblat on 2010-06-10
I got a virtual machine running and can connect to my local network, including my router.  The problem I have now is that I cannot get past the router.
I can ping another computer on my network.  
I can ping the router at 192.168.1.1, but if I ping anything past that, I get "Destination Host Unreachable."
I'm using Ubuntu 10.04 on a 64-bit machine and a Tomato router on wrt-54g (via wire).  I can ping the virtual machine from the router and can ping the router from the virtual machine.  I don't see anything on the router that would block the connection, but it appears that I am missing something.

I would appreciate suggestions of where to look, what to try.

Thanks,
Herb

---

### Post by hroitblat on 2010-06-10
The problem was that the route top the gateway was not set correctly.  I fixed it using the route command.  Now is the virtual machine question as to why it was set incorrectly.  I will look into that.

---

