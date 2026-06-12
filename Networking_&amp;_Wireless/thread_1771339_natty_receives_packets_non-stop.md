---
title: "natty receives packets non-stop"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by pyros2 on 2011-05-30
hello,

i recently bought some pre-paid internet simcard and a modem. all works fine in natty, except that i seem to be receiving packets constantly. i installed bmon so i could check the traffic, but apart from information about receiving/transmitting it doesn't say much. how can i check what applications are using the connection so i could disable them.
on windows 7, there's no such situation, but i'm not sure how precise is the traffic monitoring application.
over all received data doesn't seem to be that much, about 1 MiB/minute, but since i'm on pre-paid service i'd like to cut that down.

thanks for any help.

---

### Post by pyros2 on 2011-05-30
EtherApe shows that all these packets come through udp-unknown protocol, details show data coming from some 30 addresses. none of these addresses is familiar to me.

---

### Post by pyros2 on 2011-05-30
i believe i found what is causing the problem, it is the java process. now, killing it won't do because it comes back, stopping it produced better results. i no longer receive packets. but, i'm not sure that is a normal behaviour. could someone confirm this please.
removing java completely seems rather extreme. is there a way to disable or restrict the process, temporarily?

---

