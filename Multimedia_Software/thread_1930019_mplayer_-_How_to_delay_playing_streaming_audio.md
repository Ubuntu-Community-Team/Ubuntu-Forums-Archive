---
title: "mplayer - How to delay playing streaming audio ?"
date: 2012-02-22
forum: Multimedia Software
---

### Post by Praval on 2012-02-22
Hi,

I am using mplayer to play RTP stream (AAC encoded audio). I would like to delay playing out audio by 2-3 seconds. What command line parameters can I use?

Thanks,
Praval

---

### Post by andrew.46 on 2012-02-23
I am not sure if this is what you want but perhaps some of variation of the following:

```

sleep 3s && \
mplayer ...............................

```

Obviously replace '............' with your normal MPlayer command :).

---

