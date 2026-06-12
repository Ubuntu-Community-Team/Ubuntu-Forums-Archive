---
title: "Iptables-restore no command specified"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by niels_linux_forum on 2012-01-27
Hey everybody,

I'm having some issue on an older version of Iptables version 1.4.2

I'm using this command : iptables-restore < /etc/network/iptables.config

And the content of the iptables.config file is :

```
*filter
# -P INPUT ACCEPT
# -P FORWARD ACCEPT
# -P OUTPUT ACCEPT

-A INPUT -i lo -j ACCEPT
-A OUTPUT -o lo -j ACCEPT

-A INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT --src x.x.x.x

-A INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT --src x.x.x.x

-A INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT --src x.x.x.x
-A INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j DROP

-A INPUT -j REJECT
-A FORWARD -j REJECT

COMMIT
```

I've used this exactly the same config for another server and there I did't got any troubles.
But now I got this output:

iptables-restore v1.4.2: no command specified
Error occurred at line: 16
Try `iptables-restore -h' or 'iptables-restore --help' for more information.

I already truncated the file line endings, commenting out some rules but still didn't work.
And it always throws the error/exception.

Anybody had the same experience or anybody some advise ?

Thanks a lot in advance!

---

