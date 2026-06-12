---
title: "run stunnel4 as non-root user"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by RikoW on 2009-05-29
Dear all,

does anybody know, how I run stunnel4 in client mode without root privileges?
When I try to run it with my regular user acount, e.g.

```
> stunnel4 /home/wichmann/.stunnel
```

It just returns to the command line without error, but also without opening the stunnel. It only works with

```
> sudo stunnel4 /home/wichmann/.stunnel
```

As a (temporary) work-around, I set the suid-bit on /usr/bin/stunnel4. Now I can also run it as user "wichmann". However, I'm not happy with this solution. The user "wichmann" is in the "stunnel4" group. I would assume, that takes care of all permissions, but obviously not. Google didn't help me much :(

Thanks and cheers,

       Riko

---

