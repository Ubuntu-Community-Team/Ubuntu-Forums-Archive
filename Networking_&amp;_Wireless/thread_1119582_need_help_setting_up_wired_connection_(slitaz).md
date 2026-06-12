---
title: "need help setting up wired connection (slitaz)"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by billgoldberg on 2009-04-08
I got this old computer from a friend that I want to use as a server but it I can't get networking working.

lspci says the network card is a

3com corportation 3c905B 100BaseTX [Cyclone] (rev24)

ifconfig only list "lo".

Ifconfig -a only list "dummy0" and "lo".

Is the card no longer supported?

How can I get it working?

---

### Post by MaindotC on 2009-04-08
Post the output of:
```

lshw -C network
lspci
lsmod

```

I know you already checked lspci but I'd like to have a look just for kicks.

---

### Post by billgoldberg on 2009-04-08
> **strAlan said:**
> Post the output of:
```

lshw -C network
lspci
lsmod

```

I know you already checked lspci but I'd like to have a look just for kicks.

After posting the OP I kept googling and found out I had to load the driver module manually.

So for future users with the same problem, this is how I fixed it.

In a terminal:

modprobe 3c59x

(as root)

then I did

ifconfig eth0 up

and used the slitaz netbox tool (add eth0 (just type in eth0), then go to configure and start the service).

Pinged google and all was good.

---

### Post by MaindotC on 2009-04-08
Good.  I figured it was a module issue and sorry I couldn't have gotten to the bottom of your issue sooner.

---

