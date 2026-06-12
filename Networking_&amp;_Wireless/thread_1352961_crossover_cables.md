---
title: "crossover cables?"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by shrimpboi13 on 2009-12-12
i'm trying to get my laptop (intrepid) and desktop (karmic) networked using a crossover cable i have tried a bit of fiddling with the network manager and the help files to no avail. can anyone steer me in the right direction (if it is possible at all). thanks in advance.

---

### Post by issih on 2009-12-12
Set a static ip address on both machines:

I suggest a subnet mask of 255.255.255.0 and something like:

192.168.0.1 and 192.168.0.2 for the two machines.

Provided you have no clashing ip addresses coming in from wireless...if so switch the 0 for a 1 or a 2 or a 3 etc.....until you are clear of any other networks you have connected.

Once thats done and you have them connected by a crossover cable (it MUST be a crossover) you should be able to ping one machine from the other.

After that you need to decide what protocols you want to use.
If either machine is windows based you probably want to use samba to share things (which can be done from ubuntu by just right clicking on a folder in file manager and selecting the sharing options)

Any windows shares already set up on the other machine should be visible from ubuntu's places menu.

If both machines are unix based, its probably easiest to install the openssh server package and use the connect to server option.

Hope that helps

---

