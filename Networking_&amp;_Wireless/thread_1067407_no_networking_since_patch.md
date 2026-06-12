---
title: "no networking since patch"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by kcihtred2 on 2009-02-11
ok, i was able to get the first bunch of patches with ubuntu 8.10, but now i cannot connect hard wired...
heres my system specs:
Wifi: TRENDnet TEW-623PI
Mobo: BIOSTAR TForce TP43D2A7
CPU: C2Q Q6600
Video Card: Nvidia 8800GT

are there just not any patches for this or what?  or should i just go wireless, if so what are the terminal commands for ndiswrapper or whatever program i can use for my wireless

---

### Post by cariboo on 2009-02-11
Open an Applications-->Accessories-->Terminal and type:

```
sudo lswh -C network
```

the above command will list all your network adapters and whether the drivers were loaded.

Paste the output in your next post.

Jim

---

