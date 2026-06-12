---
title: "Network Bridge Question - 2 Ethernet Ports on Motherboard"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by Anlace on 2009-10-05
Greetings,

I have searched the forums and Google for an answer to this question with no luck so far.

How do I bridge 2 ethernet connections on the same motherboard?

I have a nForce 780i motherboard with dual ethernet ports that works great with Nvidia's drivers in Windows (XP, Vista, and 7).  The connection speeds are really fast and reliable which is why I want to be able to do the same in Kubuntu since it is the OS I prefer to work in.

Connection speeds are extremely slow in Kubuntu unless I physically unplug one of the cables, then it works alright though still slower than when I am booted into one of my Windows installations.

I've found lots of online direction about how to bridge everything from separate or virtual computers to gaming consoles, will these directions work if the 2 ethernet ports in question are on the same motherboard?  Should I treat them as if they weren't?

Even being able to permanently disable one of the ethernet ports in Kubuntu would work better than all of this plugging and unplugging.  I'm not crazy about diving under my desk.

Thanks for any and all useful suggestions.

---

### Post by never say never on 2009-10-05
Hello!  I don't think you want to create a "Bridge", but I believe you wish to "Bond" or "Team" two NICs to act as one.  In Networking a bridge is similar to a router and is used to pass traffic between separate networks without consuming an IP.  If you bond or team nics, they "Become one" and your available bandwidth and throughput is increased.  Make sure your switch supports bonding or teaming or bad things can happen.  Here is a guide that you may find helpful.  [http://www.cyberciti.biz/tips/linux-bond-or-team-multiple-network-interfaces-nic-into-single-interface.html](http://www.cyberciti.biz/tips/linux-bond-or-team-multiple-network-interfaces-nic-into-single-interface.html)  If that guide is not helpful try searching for "Linux bonding nics"  Hope this helps!

---

### Post by Anlace on 2009-10-06
Greetings,

This info is very helpful, thank you very much!

---

