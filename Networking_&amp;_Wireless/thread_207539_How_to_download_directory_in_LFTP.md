---
title: "How to download directory in LFTP?"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by cnspy on 2006-07-02
How to dowload the directories with has special word using lftp?

such as:

How to download the directories with "exam"?

*.exam.*


Thanks in advance.

---

### Post by tomchuk on 2006-07-02
Try wget:
```

wget -m "ftp://server.whatever.com/*.exam.*"

```

---

