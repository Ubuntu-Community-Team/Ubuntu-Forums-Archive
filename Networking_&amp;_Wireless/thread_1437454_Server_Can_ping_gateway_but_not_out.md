---
title: "Server Can ping gateway but not out"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by terbor on 2010-03-23
I am trying to figure out what I did to my connection.  All files seem right, the gateway is set right, I can ping the gateway, however I cant seem to ping my server.  i know the Internet connection is good, I can ping out with other servers and the physical connections haven't changed since this issue started.  I lost power, all my servers rebooted and this one isnt able to come back online.  Any suggestion?  Thanks in advance.

---

### Post by Aped on 2010-03-24
It would be helpful if you could list the relevant info here for us, in [code] tags if you could, the results of:
`ifconfig` - especially to make sure it's being properly assigned an ip and whatnot
`lspci`
maybe some pings (internal/external) 
and of course the type of router/gateway and network device you're using.

---

### Post by Iowan on 2010-03-24
Check (post) results of **route -n**. Are you pinging by name, IP address, or both? (Wondering about DNS problem.)

---

### Post by terbor on 2010-03-24
It ended up being the resolv.conf file.  I thought I set that right ... but I guess not.  Thanks for you help though.

---

### Post by Iowan on 2010-03-24
> **Iowan said:**
> (Wondering about DNS problem.) */etc/resolv.conf* was next on the list. :D
Glad you found it!
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

