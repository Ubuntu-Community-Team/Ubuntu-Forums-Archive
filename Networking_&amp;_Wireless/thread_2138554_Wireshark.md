---
title: "Wireshark"
date: 2013-04-24
forum: Networking &amp; Wireless
---

### Post by nerdyme on 2013-04-24
Using wireshark directly as root my be dangerous...:arrow:

You can make the use of group management and user management in linux.
Create a group say "Packet".

groupadd Packet

Then add yourself to the group.

usermod -a -G Packet <username>

Now change the Group of file /usr/bin/dumpcap //responsible to read the interfaces

chgrp Packet /usr/bin/wireshark

Change the permissions of that file so that only the group members can view and read it.

chmod 750 /usr/bin/dumpcap

I think it will work. For any doubt, do post here.

---

### Post by Slim Odds on 2013-04-24
> **nerdyme said:**
> Using wireshark directly as root my be dangerous...:arrow:

You can make the use of group management and user management in linux.
Create a group say "Packet".

groupadd Packet

Then add yourself to the group.

usermod -a -G Packet <username>

Now change the Group of file /usr/bin/dumpcap //responsible to read the interfaces

chgrp Packet /usr/bin/wireshark

Change the permissions of that file so that only the group members can view and read it.

chmod 750 /usr/bin/dumpcap

I think it will work. For any doubt, do post here.
This will NOT make wireshark RUN as root and therefore will not work for the purpose stated in this thread.

---

### Post by nerdyme on 2013-04-24
> **Slim Odds said:**
> This will NOT make wireshark RUN as root and therefore will not work for the purpose stated in this thread.

Actually I had done this way and it worked. It will show up all interfaces and packets will be captured. What else we need?

---

### Post by nerdyme on 2013-04-24
> **pat_bateman said:**
> or press ALT+F2 and type:
```
gksudo wireshark
```

-Pat

Can't I change the permission of /usr/bin/dumpcap instead of running it as root.

---

### Post by wildmanne39 on 2013-04-24
*Thread moved to **Networking & Wireless**.* 
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

