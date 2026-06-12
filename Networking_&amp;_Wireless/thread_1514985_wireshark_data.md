---
title: "wireshark data"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by spezticle on 2010-06-21
i'm using wireshark and in a live capture i've used the filter arp.
i'm noticing that a particular computer on my network is constantly doing this:

```

time         source          destination   protocol    info
17:08:46     192.168.1.2     Broadcast     ARP         Who has 192.168.1.4?  Tell 192.168.1.2



```

and when i mean constantly, i mean at least 30 times per second, where the info "Who has" ranges from 192.168.1.1 through 255.

i'm new to wireshark and i have no idea how to understand this data... any insight as to what is going on?

---

