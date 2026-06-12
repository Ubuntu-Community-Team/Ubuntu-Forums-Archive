---
title: "i need to check if my wifi card is broken."
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by bradpurvis on 2009-08-05
it has worked on almost every ubuntu realease including 9.04 which is what i am using now.

it just randomly stopped working can someone give me a command that can check for hardware issues?

---

### Post by pastalavista on 2009-08-05
It sounds like somebody switched your wireless off manually... look for a switch.

but try these commands in terminal ```
lshw -c network

lspci | grep 802.11

ifconfig
```

---

