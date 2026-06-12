---
title: "uShare thinks eth0 is down"
date: 2008-11-18
forum: Multimedia Software
---

### Post by glittalogik on 2008-11-18
I have uShare on my machine to share video with my Xbox; it worked perfectly on Hardy but since I upgraded to Intrepid I've been having problems.

When I load uShare I get:
> Interface eth0 is down.
Recheck uShare's configuration and try again !

but ifconfig shows eth0 as connected and working, and everything else (samba shares, internet etc.) seems to be fine.

ushare.conf as follows, pretty much exactly the same as before the upgrade:
> # /etc/ushare.conf
USHARE_NAME=unifex
USHARE_IFACE=eth0
USHARE_PORT= 49200
USHARE_TELNET_PORT= 49201
USHARE_DIR=/home/conrad/Videos
USHARE_OVERRIDE_ICONV_ERR=yes
ENABLE_WEB=yes
ENABLE_TELNET=yes
ENABLE_XBOX=yes
ENABLE_DLNA=

Any suggestions?

---

### Post by goldfish2 on 2008-11-18
When you start Ushare, does it still work though?  I've heard many say on these forums that they get that error, but that it still works regardless.  Guess it is some non-fatal issue.

GoldFish

---

