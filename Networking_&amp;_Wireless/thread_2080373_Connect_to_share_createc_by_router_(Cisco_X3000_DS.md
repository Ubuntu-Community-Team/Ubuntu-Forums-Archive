---
title: "Connect to share createc by router (Cisco X3000 DSL router)"
date: 2012-11-03
forum: Networking &amp; Wireless
---

### Post by bigwoof on 2012-11-03
Hi There,

I have been trying to connect my linux machines to the share created by my router (Cisco X3000 DSL router).  It is a 1TB USB drive connected by USB - if that is important to know.

I set up the share in router setup and I can see it on the network if I use:

```
smbtree -N
```
which gives me:
```
WORKGROUP
	\\CISCO02437     		DSL Gateway
cli_start_connection: failed to connect to CISCO02437<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
```

When I browse to through the file manger and select "WORKGROUP" under "Windows Network" I get:

```
Unable to mount location

Failed to retrieve share list from server
```

I have little experience with networking and it all seems like black magic to me.

Anybody know how to get my machine to connect?

Cheers

Phil

---

