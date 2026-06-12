---
title: "Ubuntu unable to use multiple name servers"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by sohelmk on 2010-06-22
I found one strange issue with ubuntu, can anyone suggest if its a bug or as  designed?
If I have two nameservers in my resolv.conf, ubuntu only checks the  first (and receives a ‘not found’ reply from there) and never goes to  the next two nameservers. This behaviour is very different from windows  or other linux systems.

---

### Post by moiktran on 2010-07-07
sohelmk, I have been facing the same issue as well. I am using Ubuntu 10.04.

---

### Post by Iowan on 2010-07-07
I'm not sure I completely understand it, but...
> ... (The algorithm used is to try a name server, and if the  query  times out, try the next, until out of name servers, then repeat trying all the name servers until a maximum number of retries are made.)
The **man resolv.conf** page makes it sound (to me, at least) like successive nameservers are tried until one responds. If the first one responds with "not found", it has still responded. 
As I mentioned (or at least suggested), I could be 100% wrong in that interpretation...

---

### Post by sohelmk on 2010-07-14
Thanks a lot Iowan,
You are right about the algorithm, but in this case the problem is not "timeout" but "not found"
Let me give an example:

I am connected on a LAN, domain is domain1 and its name server gets added to resolv.conf when i connect to network. So now i can ping any server of domian1.

Now I connect using VPN to another network domain2. So its nameserver gets appended on top. So now i can ping any server on domain2. 

But now if I ping to any server of domain1, the nameserver of domain2 responds first without any results. So it does not try the other one. I assume if nameserver of domain2 had timed out it may have done what you said.

In this case we have tested the same thing on windows and mac OS, they work as desired, but ubuntu is giving this issue. Only solution seems adding all servers to hosts or running another named server locally.

Let me know if you need any other details, i dont know how to debug this further as ping just gives short error "unknown host"

Thanks a lot,
Sohel

---

