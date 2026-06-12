---
title: "Binary netcat variant for Ubuntu"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by MrQuincle on 2009-04-08
Dear all,

On the moment I am sending TCP/IP packets by using this construct:

```
echo "\u10 \u2 \u3 \u5 \u10 \u2 \u0 \u6" | ascii2uni -aV -q -p | nc localhost 3333
```

This works, but I would like to be able to send packets like "\u10 \u2 \u3 \u5" in an interactive manner. So, write them on stdin and then they are passed through whatever is needed, say ascii2uni and end up via netcat or telnet on the proper address.

Kind regards,

Anne

---

