---
title: "Network manager doesn't auto-connect auto-eth0 / wired connection"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by Jags_FL on 2010-05-18
even though Network-Manager > Edit Connections > Auto eth0 > Edit _is set to_ > "Connect automatically" in Ubuntu Lucid 10.04 64-bit (under Virtual Box), still after every re-boot I have to manually click network manager > auto eth0 to connect.

Many thanks in advance, any help is greatly appreciated.

---

### Post by Thanat0s on 2010-05-18
Hi,

Same problem here but I have to put "sudo dhclient" in the terminal every time I start my computer when using wired eth0.

And Firefox is always in "offline" mode when starting because it isn't aware of the connection. Very annoying...

I hope someone know how to fix this.

Thanks.

---

### Post by LordRifter on 2010-06-02
I'm having the same issue. Any ideas?

---

### Post by Thanat0s on 2010-06-03
I just fixed that 5 minutes ago.
Edit the "Auto eth0" connection and in the IPv6 settings set the method to "Ignore" (I'm not sure of english names because I'm French).

---

### Post by jsabater on 2011-02-17
> **Thanat0s said:**
> I just fixed that 5 minutes ago.
Edit the "Auto eth0" connection and in the IPv6 settings set the method to "Ignore" (I'm not sure of english names because I'm French).

I have the same issue mentioned in this post (also with IPv6 disabled). --> Lucid 32bit
It is very annoying since to log in I have to authenticate into a Network Domain. Has anyone else solved this issue?

---

