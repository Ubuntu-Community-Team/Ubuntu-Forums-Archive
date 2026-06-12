---
title: "creating a network."
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by orky7 on 2011-07-05
hi i have a ip range 192.168.0.0/24, how i can distribute this class c network into different network(each representing different departments, 64 departments can be consider) each having at least 400 hosts. i think superneting will be used here am i right? but how. or in other words combine 64 class c networks each having at least 400 hosts

thank you.

---

### Post by helgman on 2011-07-05
Try [http://www.techrepublic.com/article/ip-subnetting-made-easy/6089187](http://www.techrepublic.com/article/ip-subnetting-made-easy/6089187)

I've not read the whole piece but it seems to hold all the information you're looking for.

Please let us know if there's something that's unclear.

Regards,
Helgman

PS. Making 192.168.0.0/24 accommodate 64x400 users might prove a pain ...

---

### Post by orky7 on 2011-07-05
> **helgman said:**
> Try [http://www.techrepublic.com/article/ip-subnetting-made-easy/6089187](http://www.techrepublic.com/article/ip-subnetting-made-easy/6089187)

PS. Making 192.168.0.0/24 accommodate 64x400 users might prove a pain ...

not much of a help, i have to use two network for one department as then number of host will be 510

---

### Post by helgman on 2011-07-05
> **orky7 said:**
> not much of a help,

Did you read through the link? Nothing? No help at all?

Hrm ...

How about this:

Use your idea about combining two class C networks from the 192.168.0.0/16 address range (since I hope you are allowed to use more than the /24-network you referred to in your first post).

Combining these networks will give you a new subnet mask (find the mask that holds all the bits they have in common beginning for the right-most bit). Use two networks that are in sequence, like 192.168.0.0/24 and 192.168.1.0/24.
[LIST=1]
[*]Use the "new" subnet mask to "mask" the first network address (binary conversion is often the easiest way to do this if you're a beginner).

[*]That will give you the "network part" and the "host part" (left-most part = network part).

[*]Change only the network part. And change only the network bits in the third octet (that is the 0 between 168 and the last 0).* 

[*]Repeat until you have the required number of subnets.
[/LIST]
[SIZE="1"]* Or you might be going into public territory (see RFC 1918 for an explanation).[/SIZE]

It really doesn't matter if your "subnetting" or "supernetting". "Supernetting" a class C network is like "subnetting" a class B network ...

Regards,
Helgman

---

