---
title: "Port Forwarding?"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by TheFireTruck on 2011-07-09
I'm using a Netgear WN1000 router, and I'm trying to forward a port for a game through Dosbox (Masters of Orion 2). I set the port for 34354, and I haven't had any luck so far when trying to connect with my brother. 

In fact, I've been using this tool to check it out: [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) and it is telling me that the port isn't even open. Is this tool faulty for ubuntu? Or is there some other part of the port forwarding process that is necessary on an ubuntu system (I'm using 11.04 if you're curious).

Thanks!

---

### Post by Dangertux on 2011-07-09
> **TheFireTruck said:**
> I'm using a Netgear WN1000 router, and I'm trying to forward a port for a game through Dosbox (Masters of Orion 2). I set the port for 34354, and I haven't had any luck so far when trying to connect with my brother. 

In fact, I've been using this tool to check it out: [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) and it is telling me that the port isn't even open. Is this tool faulty for ubuntu? Or is there some other part of the port forwarding process that is necessary on an ubuntu system (I'm using 11.04 if you're curious).

Thanks!

Check the following things

1 -- Are you forwarding the correct port? 

2 -- Are you forwarding it to the correct IP

3 -- Are you forwarding the protocol needed TCP or UDP or both?

4 -- Are you running UFW on your Ubuntu System
```

sudo ufw status

```

If yes -- are the correct ports / protocols allowed 

5 -- Is it a range of ports that need forwarding or just a single port?

6 -- Is the service binding to the port/interface it's supposed to? (netstat will help determine this)

That should get you started and give you some ideas for troubleshooting.

---

### Post by TheFireTruck on 2011-07-09
Thanks so much for your quick response, here're my answers going down the list

1. Yes.
2. Yes.
3. UDP.
4. Nope, should I?
5. Just one.
6. Hmmm, I've never used netstat and I was a bit at a loss for what to do, but I ran it as 'netstat --numeric-ports' and I couldn't find any programs with the port 34354, (I just looked at the options and assumed a certain option was port, it was very unscientific) that I was looking for (the game is running)

thanks again!

Oh also, in case it's important, I might as well mention that I followed a guide to set up a static IP before I portforwarded

---

### Post by Dangertux on 2011-07-09
> **TheFireTruck said:**
> Thanks so much for your quick response, here're my answers going down the list

1. Yes.
2. Yes.
3. UDP.
4. Nope, should I?
5. Just one.
6. Hmmm, I've never used netstat and I was a bit at a loss for what to do, but I ran it as 'netstat --numeric-ports' and I couldn't find any programs with the port 34354, (I just looked at the options and assumed a certain option was port, it was very unscientific) that I was looking for (the game is running)

thanks again!

Oh also, in case it's important, I might as well mention that I followed a guide to set up a static IP before I portforwarded

Try this netstat command

```

sudo netstat -alnp

```

---

### Post by TheFireTruck on 2011-07-10
Okay I got it, so it is indeed forwarding to 34354 but this is what the entry looks like:

```
udp        0      0 0.0.0.0:34354           0.0.0.0:*                           2181/dosbox     
```

Where the 0.0.0.0 is, the other files on netstat show my internal IP.

---

### Post by TheFireTruck on 2011-07-13
Anyone have any ideas?

---

