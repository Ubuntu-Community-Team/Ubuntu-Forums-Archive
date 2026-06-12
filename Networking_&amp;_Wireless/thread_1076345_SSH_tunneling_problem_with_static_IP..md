---
title: "SSH tunneling problem with static IP."
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by cb951303 on 2009-02-21
I have a VPS located in another country that me and my friends use mainly for SSH tunneling.

For me, it works without a problem when I connect to it like this
```

ssh -D [PORT_NUMBER] user@server.address

```

auth.log shows this
```

Feb 21 10:08:23 83 sshd[20495]: Accepted password for [USER] from XX.XX.XX.XX port 19375 ssh2

```

but my 2 friends connect from windows boxes. one has a dynamic IP (like me) and the other one has static IP. For the one with dynamic IP, auth.log shows a similar result but for the one with static IP it gives this
```

Feb 21 10:08:23 83 sshd[20495]: reverse mapping checking getaddrinfo for dsl.staticXXXXXXXX.-----.net failed - POSSIBLE BREAK-IN ATTEMPT!
Feb 21 10:08:23 83 sshd[20495]: Accepted password for [USER] from XX.XX.XX.XX port 19375 ssh2

```
and as a result he can't use the tunnel. 

Does anyone know what's this about and how to solve it?

Thanks

---

### Post by mpokrywka on 2009-02-23
Your friend's reverse dns is not configured correctly (friend's ISP's fault).

Add:
**UseDNS no**
to /etc/ssh/sshd_config (on VPS of course)

---

### Post by cb951303 on 2009-02-23
Thanks.
First I disabled reverse dns check with your help but then I thought adding the host manually to do /etc/hosts and now it works with dns checking enabled :popcorn:

---

