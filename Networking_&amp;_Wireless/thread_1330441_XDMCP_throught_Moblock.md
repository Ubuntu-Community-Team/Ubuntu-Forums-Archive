---
title: "XDMCP throught Moblock"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by papalagi on 2009-11-18
hi everybody

i have an headless karmic 64-bit server i access via:

```
X :1 -query 192.x.x.x
```

everything works just fine as long as Moblock is not running, here is my

```
# blockcontrol.conf - configuration file for blockcontrol

# This file is sourced by a shell script. Any line which starts with a # (hash)
# is a comment and is ignored. If you set the same variable several times,
# then only the last line will be used.

# Refer to blockcontrol.defaults (/usr/lib/blockcontrol/blockcontrol.defaults)
# for the complete set of possible configuration variables with comments.

# Do a "blockcontrol restart" (sometimes even "reload" is enough) when you have
# edited this file.

WHITE_TCP_OUT="http https ssh 6000:6005"
WHITE_UDP_OUT="177"
WHITE_UDP_IN="177"
WHITE_TCP_IN="6000:6005 http ssh"

```


as you can see i've whitelisted the ports i think XDMCP should use, but when i try to connect i stand facing a black X screen with no trace of login options

any help please?

regards

---

