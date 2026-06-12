---
title: "Fast network sharing"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by Earnol on 2010-07-01
I have ubuntu server x64 installed on quite slow intel atom cpu.

It has gigabit lan and if i connect to this pc via samba it works ok. Very fast.

Now i want to share directory on ubuntu server. I've opted to sftp solution, but it does not work with high bandwidth, CPU could not work with high stream.
Desired network configuration:
server <--> NAT router(hardware) <--> corporate network <--> NAT router(hardware) <--> PC
Routers has port forwarding. All routers has fixed IP and IP should be prove of authentication token. I know it is not secure, but in this particular case security is not an issue.
I do not care if my data will be intercepted by third party, i only care about speed.
I wonder are there any solution that satisfy my needs?

---

