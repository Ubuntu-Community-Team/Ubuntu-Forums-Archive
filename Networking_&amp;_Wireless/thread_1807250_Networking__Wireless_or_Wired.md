---
title: "Networking  Wireless or Wired"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by rvhodge@northlc.com on 2011-07-18
I had ubuntu installed on July 1, 2011, everything worked until yesterday July 17, 2011. Now I can not connect to the internet wired or wireless. Can someone help. My Hp was formerly running Windows Vista. I needed to change. This seemed to be the best option. Thanks Bob

---

### Post by nm_geo on 2011-07-18
> **rvhodge@northlc.com said:**
> I had ubuntu installed on July 1, 2011, everything worked until yesterday July 17, 2011. Now I can not connect to the internet wired or wireless. Can someone help. My Hp was formerly running Windows Vista. I needed to change. This seemed to be the best option. Thanks Bob

Bob,

We are going to need more info for sure.  In terminal copy and paste then copy the results back to the thread.

```
uname -a
```

```
lspci -nn | grep 0280
```

```
sudo lshw -C network
```

```
lsmod
```

If you paste result between the # sign or highlight your results and hit the # sign it will do the boxes.

---

