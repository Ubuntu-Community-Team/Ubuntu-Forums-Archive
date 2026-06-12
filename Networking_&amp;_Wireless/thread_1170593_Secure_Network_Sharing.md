---
title: "Secure Network Sharing"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by tdreyer1 on 2009-05-26
Right now, I have a hardware raid array (1 TB) serving as my multimedia repository. This array is connected to my computer via e-SATA and is encrypted using true-crypt.

What I want to do is migrate this setup to a new, headless, dedicated computer on my network (a media server essentially). What I need is complete security on each step of the way (and I mean paranoid security).
[LIST]
[*]When the new machine boots up, It should not automatically mount the encrypted media disk, regardless of whether or not it was mounted previously. 
[*]The disk should be mounted when I tell it to from another machine.
[*]This disk needs to be shared over the local network (securely)
[*]the network share should be password protected
[*]the network share should be accessible by both Linux and windows machines
[/LIST]

Basically, I want to set up *secure* network storage, but I don't know where to look/research to get started. Also, an all-in-one NAS storage solution would work, but I haven't found anything that does what I want (security-wise).

Any Ideas?

---

### Post by albinootje on 2009-05-26
> **tdreyer1 said:**
> 
[*]This disk needs to be shared over the local network (securely)
[*]the network share should be password protected
[*]the network share should be accessible by both Linux and windows machines

Use ssh (and then WinSCP on the windows clients) for the shares, or use OpenVPN for all traffic between server and clients.

---

### Post by whoop on 2009-05-26
Well as a bare minimum: (key based) ssh, scp and any form of disk encryption would suffice. That would make it really simple and really secure...

For some all-in one nas solution: did you check out FreeNAS? I believe it even has disk encryption, and is highly configurable.

---

