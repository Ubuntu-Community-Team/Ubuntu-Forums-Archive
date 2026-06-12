---
title: "Video card datas: how to find?"
date: 2006-07-16
forum: Multimedia &amp; Video
---

### Post by carontis on 2006-07-16
I'm looking for something that can show me all exact datas about my video card. Well, I know it's a S3 Savage4, but I need to know all datas. Is there something that can help me? Thanks.

---

### Post by tseliot on 2006-07-16
> **carontis said:**
> I'm looking for something that can show me all exact datas about my video card. Well, I know it's a S3 Savage4, but I need to know all datas. Is there something that can help me? Thanks.

```
lspci | grep VGA
```

and

```
lspci -n | grep 0300
```

---

