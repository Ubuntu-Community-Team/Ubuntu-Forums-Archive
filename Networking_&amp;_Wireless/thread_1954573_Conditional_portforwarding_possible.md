---
title: "Conditional portforwarding possible"
date: 2012-04-08
forum: Networking &amp; Wireless
---

### Post by Blunzen Sepp on 2012-04-08
Let me desribe the problem first:
My server application "Blunzen's App" listens on port 1234 for client requests which works fine for nice clients. But there are also evil "Blunzen's App" clients that destroy my server. Unfortunately my "Blunzen's App" server is silly and therefore not able to distinguish good from evil. I can't change the "Blunzen's App" server protocol to make it smarter to defend itselves.

And here is my solution idea:
I want to invent a "Blunzen's App Guard" service that listens on port 1234, that, instead of the "Blunzen's App" server, checks client requests for good and evil and only forwards the good requests to the "Blunzen's App" server that now listens on port 4321.
The good clients show a permit to the "Blunzen's App Guard" service. With a valid permit all packages from a good client should be forwarded to port 4321. All bad requests should be ignored.

Suggestions for implementation are welcome.

---

### Post by iponeverything on 2012-04-08
what is with all the homework requests lately.

---

### Post by kevdog on 2012-04-08
A port knocker utility is one possibility.  The client would send a "combination" that would unlock the port and the port would open for that client's IP address specifically -- requires use of firewalls.

If you don't want something that complex, you could really lock down the port to specific IP addresses or usernames through just using a firewall itself.

---

### Post by roelforg on 2012-04-08
I'm not gonna do your homework.
But if the good clients always have the same ip, just make some firewall rules.
That's the way my private git repo is secured. (only 3pc's can even see it)

---

### Post by Blunzen Sepp on 2012-04-08
> **roelforg said:**
> I'm not gonna do your homework.
But if the good clients always have the same ip, just make some firewall rules.
That's the way my private git repo is secured. (only 3pc's can even see it)

Unfortunately the IPs and also the users of the good clients  are not predictable.

---

### Post by Blunzen Sepp on 2012-04-08
> **kevdog said:**
> A port knocker utility is one possibility.  The client would send a "combination" that would unlock the port and the port would open for that client's IP address specifically -- requires use of firewalls.

If you don't want something that complex, you could really lock down the port to specific IP addresses or usernames through just using a firewall itself.

I forgot to mention that I want to keep my "Blunzen's App" as public as possible. I don't know the users and the IPs who acquire the good clients. 
Thank you for the hint with port knocking. I think that can be the solution.

---

### Post by Blunzen Sepp on 2012-04-09
> **kevdog said:**
> A port knocker utility is one possibility.  The client would send a "combination" that would unlock the port and the port would open for that client's IP address specifically -- requires use of firewalls.

If you don't want something that complex, you could really lock down the port to specific IP addresses or usernames through just using a firewall itself.


Thank you for the port knocker hint.  I think it is exactely what I need.

---

