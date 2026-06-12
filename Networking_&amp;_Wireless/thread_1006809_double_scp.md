---
title: "double scp"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by fikusadja on 2008-12-09
Hi. I have little problem with using scp. I want to copy file from remote server C to my local computer, lets say A. But I can only access to server C from another remote server B (so I need two ssh connections). Now my question is if I can copy a file from C to A without first copying it to B and then to A ? 

thanks in advance.

---

### Post by reacocard on 2008-12-09
Assuming computer A is scpable from B, just ssh to B and do something like this:
```
scp user-on-C@C:/remote/file/path user-on-A@A:/local/file/path
```

If you can't scp from B to A, then you can use port forwarding instead:
```
ssh -L 6987:C:22 user-on-B@B
```
leave that open and open another terminal:
```
scp -P 6987 user-on-C@localhost:/remote/file/path /local/file/path
```

note that you can use any valid port number instead of 6987.

---

