---
title: "cannot log into a machine via SSH with a wired connection"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by dagarshali on 2009-08-27
Hi,
I am pretty new to Linux. I am connecting to the internet via a wired connection..

I am able to connect to the one machine via ssh and not to the other. When I try the other machine, it gives the error
ssh: connect to host hpc4.iastate.edu port 22: No route to host

however, when I am connected to the internet via wireless, i am able to ssh to the very same machine..

Can you please help me..

thanks,
vishwa

---

### Post by Mark20 on 2009-08-27
When you say your are connecting to the Internet either through a wired or wireless connection, are you connecting to the same router?  Also, is hpc4.iastate.edu on your local network, or are you making a remote connection?

This seems like it could be a firewall issue, assuming that you are in fact connecting through different routers...

Mark

---

### Post by dagarshali on 2009-08-27
When I say I can't connect it is from a router (no a wireless though)...I think i know the problem..i just can't figure how to solve it..

After i posted the thread..i looked into the router, I have two computers connected to the router..

When do a ifconfig on the first one, i get 129.186.17.5 as the ip address..

but when I do the same ifconfig on my laptop, i get inet addr:10.25.50.9

I know that the hpc4.iastate.edu can accept connection only from the address like 129.186 type..

I dont understand, why the router is issuing like a local ip adress to one and not the other?

---

### Post by dagarshali on 2009-08-27
On what i call router, is written fast ethernet switch..

---

### Post by nhanquy on 2009-08-27
> **dagarshali said:**
> When I say I can't connect it is from a router (no a wireless though)...I think i know the problem..i just can't figure how to solve it..

After i posted the thread..i looked into the router, I have two computers connected to the router..

When do a ifconfig on the first one, i get 129.186.17.5 as the ip address..

but when I do the same ifconfig on my laptop, i get inet addr:10.25.50.9

I know that the hpc4.iastate.edu can accept connection only from the address like 129.186 type..

I dont understand, why the router is issuing like a local ip adress to one and not the other?

Looks like one  using static IP (fixed address 129.xxx) and the other using dynamic IP (DHCP 10.25.xxx)
You can make it fixed by configuring the IP on that machine or configuring on the router (using the PC MAC and assigning a fixed IP for it)

---

### Post by dagarshali on 2009-08-27
the switch i am using is a dlink dss-8+, could you tell how to log into the switch to change information...

---

