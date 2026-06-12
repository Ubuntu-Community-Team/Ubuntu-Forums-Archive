---
title: "GUFW - SPT / DPT Confusion"
date: 2013-06-19
forum: Networking &amp; Wireless
---

### Post by guimaster on 2013-06-19
Greetings,

 In the following rule, is Port 137 the port that the UDP packet leaves 192.168.1.1 on, or is it the port that 192.168.1.2 receives the packet on?

```

Allow - In - UDP - From: 192.168.1.1 - Port Any - To: 192.168.1.2 - Port 137

```

 Complicating things further: In the following rule, is Port 137 on 192.168.1.1 the Source Port or the Destination Port? What then is the name of Port 137 on 192.168.1.2?

```

Allow - In - UDP - From: 192.168.1.1 - Port 137 - To: 192.168.1.2 - Port 137

```

 Thanks!

---

