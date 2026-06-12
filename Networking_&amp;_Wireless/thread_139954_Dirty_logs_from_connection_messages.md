---
title: "Dirty logs from connection messages"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by dresnu on 2006-03-05
I'm connecting to the internet through an adsl/pppoe connection using an ethernet modem. I have no problems with my connection apart from the fact that after connecting(at boot) I get these strange messages ```
Inbound IN=ppp0 OUT= MAC= SRC=62.190.197.7 DST=82.54.88.137 LEN=343 TOS=0x00 PREC=0x00 TTL=52 ID=47355 PROTO=UDP SPT=0 DPT=1026 LEN=323
``` that start flooding my logs. For example if I run dmesg immediately after I boot I can read what dmesg is expected to return. If I wait a few minutes I get only lines like the one above as the output! The same happens also with /var/log/messages. At first I thought it might have been a firestarter problem, which starts at boot just like the connection, but even after disabling it I got the same behaviour. Any ideas on what is wrong, or how I can fix it?

Thanks

---

