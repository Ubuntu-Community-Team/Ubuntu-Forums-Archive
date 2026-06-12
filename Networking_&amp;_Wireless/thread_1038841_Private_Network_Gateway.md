---
title: "Private Network Gateway"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by wgcampbell on 2009-01-14
I have a private network of linux boxes and various devices attached to my (private) wireless router which gets its internet service from a semi-private wireless access point (which I can't control).

I'd like for one of the linux boxes to act as a gateway machine to forward specific ports to specific ip addresses on my internal network.  I have a "addressable" box in another location that I could reverse ssh tunnel to (if that's part of the required solution).

My question is how to set up the "gateway machine" so that accepts and properly forwards ports to the appropriate linux box or device on the internal network?

---

### Post by wgcampbell on 2009-01-15
After tinkering with reverse tunnel ssh and iptables, I discovered that the whole thing could be accomplished with remote tunnel ssh using a "bind_address".  The final solution was:

```
$ ssh -R [Offsite SSH Server IP]:[Offsite Accepted Port]:[Internal webcam IP]:[Webcam Port] [Offsite URL]
```

You must have GatewayPorts set to "yes" (in your sshd.config file) in order to effectively utilize this solution.

---

### Post by Iowan on 2009-01-16
Solved? (Mark thread [SOLVED] under Thread Tools).  Congrats!

---

### Post by wgcampbell on 2009-01-16
I would, but I don't see that option in my "thread tools"!

---

### Post by Iowan on 2009-01-16
Hmmm... maybe that went away with the Thanks.  My only threads are buried in the archives, so I don't know if the option ever existed, but it's not there now.

---

