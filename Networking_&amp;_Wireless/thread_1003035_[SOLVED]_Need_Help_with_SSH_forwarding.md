---
title: "[SOLVED] Need Help with SSH forwarding"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by metrofun on 2008-12-05
The situation is next.
I has computer connected only to external computer with ssh, that computer is only connected to another external computer, which is connected to enternet.And i want to connect through ssh to internet from first computer.
And the problem is that, a cant succeed =(
I was forwarding from local comp to second on port 22, on second from port 22 to port 22 on third...in different ways...
But it nothing...
So at last i decided to ask for help, to get step buy step solution for my specific problem.
Thanks

---

### Post by puppywhacker on 2008-12-06
Hi,

use different ports, at some point you run out of port 22's :p 

STEP 1
From comp_1 connect to comp_2 (don't disconnect) The trick is the -L creating a tunnel from comp_1 through comp_2 on to comp_3
```

ssh -L 9999:comp_3:22 comp_2

```

STEP 2
From comp_1 connect to the tunnel you created in step one. It starts on your localhost on port 9999 and terminates at your third comp on port 22
```

ssh localhost:9999

```

goodluck

---

### Post by metrofun on 2008-12-06
Cool That's that +)

Thanks a lot
P.S. only ssh localhost -p 9999 works for me

The only problem is that apt-get/synaptic don't anderstand socks, and i can't update my system +), but firefox works pretty nice with
sudo ssh -D port user_on_comp3@localhost -p 9999

---

