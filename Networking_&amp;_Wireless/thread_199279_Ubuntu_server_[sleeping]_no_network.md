---
title: "Ubuntu server [sleeping]??? no network"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by BOCTOK on 2006-06-18
Hi all,

I have had this server running for a pretty good while without a problem.  I recently had to reconfigure my network (IPCop firewall) due to the fact that my ISP made some mistakes.  Eventually, in an attempt to solve the problem, they switched me from PPPoE to DHCP.  All well and good.  But reconfiguring the server didnt go so well.  Now I have no network connection to the server.  I have tried it directly from another PC using a crossover cable, as well as through a hub, but no connection.  The connection lights on the hub dont even come on for the server.  

Logging in to the console, I get this message <date, time> [sleeping] 0 listening (0 unique), which keeps updating and prevents me from doing anything from console because it overwrites all my commands as well as the output.  I was able to run ifconfig and see that everything looks normal for the settings.

Has anyone ever had this problem and was able to fix it?  I really dont want to lose all of the data on the server with a reinstall.

Thanks in advance.

[edit] I would imagine that the "0 listening" part would mean that it is not listening on any ports.  Now, if I can only input the commands fast enough to set the ports.....

---

### Post by nick944 on 2006-06-18
it would probably fix it if u reeinstalled ubuntu

---

### Post by BOCTOK on 2006-06-18
You think?

That is what I'm trying to avoid.

I solved the problem with the "[sleeping]" message.  It was a process that needed to be killed, but I still have no connectivity (as if the computer had no NIC).

---

