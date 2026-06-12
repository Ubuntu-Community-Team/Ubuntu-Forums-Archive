---
title: "Slow Mythfrontend startup when DSL connection not working"
date: 2008-08-07
forum: Mythbuntu
---

### Post by ederopaa on 2008-08-07
Hi,

I noticed that when my internet connection was not working for a day mythfrontend was really slow starting up (around 40-50 s) on my frontend/backend machine. On my other, only frontend, computer it started normally.

Any ideas what could have caused this? 

Looking at the front end log there was a long timegap after "starting mythfrontend.real.."

Thanks!
Ede

---

### Post by managementboy on 2008-08-07
happens when your DSL router does the DHCP. When you loose the connection some routers get messed up. Since mythfrontend uses the IP provided by the router, it leads to these symptoms.

---

### Post by ederopaa on 2008-08-07
Is this true when I actually have a router (with dd-wrt software) that handles dhcp connected to separate DSL modem.

---

### Post by managementboy on 2008-08-08
> **ederopaa said:**
> Is this true when I actually have a router (with dd-wrt software) that handles dhcp connected to separate DSL modem.

all I can say is that it happens to me. As soon as my router looses DSL the IP gets weird and mythfrontend, which needs a working IP has problems.

---

### Post by lmclaren on 2008-08-13
Hi,

I had the same problems, it was due to dns configuration, from (distant) memory you need to add a record to your host table for your machine name to its fixed ip address, symptoms I seen where things like it was very slow to login via a terminal but once in it went a lot quicker.

regards

LM

---

