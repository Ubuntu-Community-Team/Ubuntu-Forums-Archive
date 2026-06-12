---
title: "Configure SSH to always bounce connections through A and B when connecting to C?"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by ipsi on 2011-01-19
Due to some serious issues we're having with our VPN at work (constantly craps out, to the extent that I can log into an SSH session and not even be able to type 'sudo' before it dies), I'd like to be able to bounce my SSH connections to a different server (A), then on to the actual server I'm connecting to (B).

For whatever reason, going A -> B is significantly more reliable than going directly go A (but not perfect).

At the moment, I have to do

```
ssh -t A ssh B
```

which gets a bit tedious to type out all the time. Ideally, I'd like to set up some form of configuration, so I can just go

```
ssh B
```

and have the connection routed through A. I'll still have to enter my password for both A and B, but this will be easier.

In addition, there are some servers that I can't connect to directly, but have to go through B first, meaning I'd have to go

```
ssh -t A ssh B

(wait)

ssh C
```

Which, again, is a bit of a pain, given that I connect to these servers a lot.

Ideally, I'd like to be able to configure SSH so that I can just go

```
ssh C
```

And have it automatically routed through both A and B.

Are either of these things possible to configure on my end, without needing an admin to touch anything on any of A, B, or C?

If you're curious, I think the reason the connection is crap is related to hideous latency given that I'm in New Zealand, and A, B, and C are all in the UK, and the IDS systems on the network where B and C doesn't like it an awful lot. But there's not an awful lot I can about that, except bounce my connection through A to minimize the latency that B sees (but increase the latency I see!).

---

### Post by ipsi on 2011-01-24
Bump. No one has any suggestions?

---

### Post by ipsi on 2011-03-17
Best I've found so far is simply going

```
ssh A -t ssh user@B -t ssh user@C -t sudo -i
```

---

