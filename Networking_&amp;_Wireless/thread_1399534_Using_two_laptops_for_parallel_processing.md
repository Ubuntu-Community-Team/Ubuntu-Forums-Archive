---
title: "Using two laptops for parallel processing"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by raj.mohan on 2010-02-05
Guys I need to do a demo in my college regarding parallel processing in OpenFOAM. So me and my team mate each has a laptop. Only two. So is it possible to simply connect both our laptops using a LAN crossover cable to run mpi? Please help.

---

### Post by Benic on 2010-04-23
The short aswer is yes. But this is where things get a little complicated. You need to set up passwordless rsh or ssh access, then modify /etc/lam/lam-bhost.def to include both laptop's IP address that can be read by each other (the one on the ethernet you're both using), set up firewall permissions (MPI use a random TCP port). Both laptops need the exact same version of lam-mpi (update included).

This is the big picture, I'm stuck somewhere near the end of the process. The two computers can communicate to each other via lam-mpi, but the second one can't be turned into a node for parallel computing. Still looking for a solution...

---

