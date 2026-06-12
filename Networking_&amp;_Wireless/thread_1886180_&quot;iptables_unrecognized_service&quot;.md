---
title: "&quot;iptables: unrecognized service&quot;"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by XEtedBear on 2011-11-24
In trying to figure out why my 2 Ubuntu systems will not talk to each other I followed advice to check on iptables status and stop it if necessary.

Synaptic Package Manager tells me iptables is installed. Any service request on iptables (start, stop, status) results in: 
```

iptables: unrecognized service

```

How do I train Ubuntu to recognize the combination of the letters i, p, t, a, b, l, e and s, in that order?

---

### Post by Doug S on 2011-11-24
I don't know about GUI versions of Ubuntu, only the server edition. To see what is going on with iptables, in a terminal window I would type:```
sudo iptables-save -c
```or type:```
sudo iptables -v -n -x -L
```
I don't know if this helps you or not. I did find your other thread about your two computers, and it is not clear what is going on, but yes I would look at your iptables as one of a few areas to check.

---

### Post by XEtedBear on 2011-11-26
Thanks for this

Both commands were accepted and produced a lot of output. none of which makes any sense to me in the context of explaining why I cannot get my 2 ubuntu systems to communicate with each other.

Further more I am surprised to find that after such a long period of investigation and posting on expert forums I have not found a single item of information which might explain this issue. Doesn't this suggest that it cannot be achieved between 11.10 and 10.10 in the configurations I am using?

---

