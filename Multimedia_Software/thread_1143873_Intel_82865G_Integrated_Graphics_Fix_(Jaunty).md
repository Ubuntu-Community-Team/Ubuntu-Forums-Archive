---
title: "Intel 82865G Integrated Graphics Fix (Jaunty)"
date: 2009-04-30
forum: Multimedia Software
---

### Post by VMC on 2009-04-30
If you installed or upgraded Ubuntu to Release 9.04 (Jaunty).

From a Terminal type:

```
lspci -nn|grep VGA
```

If the output is this:

> 00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)


Then the only fix that works for me is the [[COLOR="Red"]**Rollback**[/COLOR]]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") method.

**[COLOR="Lime"]If someone has completely restore _82865G_ by another means please report exactly how that was accomplished[/COLOR]**.

---

### Post by bulletboy on 2009-05-24
The rollback worked perfectly for me as well.
I have the same lspci output.

I posted in the rollback wiki page results section as Zippo.

---

### Post by babygenius55 on 2009-08-15
Worked for me!!!!!! I spent hours tryign to find the link in this post  BUMP!

00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)

I'm on the 5th or 6th ubuntu install on various PC's. I love learning about this shyte. It's frustrating, but wonderful when I finally find the answer.  Roll back...It took me way too long to find that.

---

