---
title: "Port-forwarding and Ubuntu"
date: 2013-06-03
forum: Networking &amp; Wireless
---

### Post by Notskal on 2013-06-03
Hello,

I've been trying to figure why forwarded ports in my router (Cisco EPC3825) won't work on my new PC. Port-forwarding worked fine in my old PC which used Vista and I had no problems. I'm new to Linux and I installed Ubuntu 12.04 (desktop version) a few days ago.

My router settings are just as they were when I used Vista and I've got a static IP address. I've tried to open several ports just for testing if they work but none of them work.

I know that opening ports should be purely router settings tweaking but I wonder if there are some configurations in Ubuntu that block port-forwarding. I've read something about iptables, are they related to port-forwarding?

Any help is greatly appreciated! :)

---

### Post by Doug S on 2013-06-03
Hi, and welcome to Ubuntu forums,

Yes, iptables is used to implement port-forwarding, however not in your case, only when the computer is also acting as a router. If I understand your case correctly, your computer should not even know the packets are port forwarded.

Could you give us a specific example of your situation? It is not clear, to me at least, why you think port forwarding is not working. A default desktop 12.04 computer would not be listening for any incoming external traffic (I think, I only run ubuntu server). Maybe you installed SSH server and want to connect via an SSH client from elsewhere. (?) Are you running a firewall on your desktop? (also typically iptables based.) Maybe it is blocking ports. Post the output from:```
sudo iptables -v -x -n -L
```

---

### Post by Notskal on 2013-06-04
> **Doug S said:**
> Hi, and welcome to Ubuntu forums,

Yes, iptables is used to implement port-forwarding, however not in your case, only when the computer is also acting as a router. If I understand your case correctly, your computer should not even know the packets are port forwarded.

Could you give us a specific example of your situation? It is not clear, to me at least, why you think port forwarding is not working. A default desktop 12.04 computer would not be listening for any incoming external traffic (I think, I only run ubuntu server). Maybe you installed SSH server and want to connect via an SSH client from elsewhere. (?) Are you running a firewall on your desktop? (also typically iptables based.) Maybe it is blocking ports. Post the output from:```
sudo iptables -v -x -n -L
```

I tested if the ports work on my old PC and they didn't so the problem is not Ubuntu. I'll keep working on the router, thanks for your reply.

---

### Post by lisati on 2013-06-04
Is your new computer being assigned the "correct" IP address?

---

### Post by Notskal on 2013-06-05
> **lisati said:**
> Is your new computer being assigned the "correct" IP address?

Yes, it sure is.


Anyway got some ports working by using some PSI port-forwarder, a lightweight program. It helped a lot but I'm still struggling with some other ports.

So yeah Ubuntu is not the problem, something else is.
Thanks for your replies, see ya!

---

