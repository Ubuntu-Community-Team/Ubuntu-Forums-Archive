---
title: "Flac to Flac conversion"
date: 2008-12-23
forum: Multimedia Software
---

### Post by clk99 on 2008-12-23
Hi, quick question. Is there a command-line program out there for flac to flac conversion?  I have some invalid flac files that I'd like to try repairing. 

Thanks.

---

### Post by jpkotta on 2008-12-24
```
flac -d bad.flac && flac bad.wav -o good.flac
```

---

