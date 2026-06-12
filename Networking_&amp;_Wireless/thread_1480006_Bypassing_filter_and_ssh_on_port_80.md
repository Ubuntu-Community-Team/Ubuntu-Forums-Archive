---
title: "Bypassing filter and ssh on port 80"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by freakazo on 2010-05-11
Hi all, I'm having some trouble finding a way to get the following working:

I'm behind a very restrictive firewall, it only allows traffic going through port 80. So to get pass it I'm planning to create a socket tunnel through ssh (If that is the right terminology).

I'm specifically having trouble setting up ssh on my server to use port 80. or in other terms, I can't connect to my ssh server on port 80!

I added 
"port 80
Port 22"
to the sshd_config file. But still no luck. I also have a webserver running which apparently will make a difference, so how would I go about bypassing that limitation or is the reason I can't connect some other problem?

---

### Post by freakazo on 2010-05-11
Also, the server has 3 spare IP adresses so I can tell it to forward port 80 to 22 if it's destined for one of the spare Ip's.
I'm guessing here and I have no idea how to accomplish the above.

---

