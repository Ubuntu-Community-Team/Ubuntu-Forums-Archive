---
title: "X-forwarding: local copy executes rather than remote copy"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by davidflynn on 2009-02-01
Hi guys,
I'm connecting to a remote server by SSH with compression and X-forwarding enabled as:
```
ssh -XC david@some.remote.location
```

What I want is for binaries to execute on the remote server, with the GUI displayed on my local workstation. I have tried launching it from an interactive shell as above, and also tried specifying the executable as a parameter of the ssh command.

This works great *unless* the same binary is also available on the local machine. Rather than running on the remote server, it just launches the local copy of the executable on my local workstation. Argh! :mad:

How do I stop this happening? 

Dave

---

