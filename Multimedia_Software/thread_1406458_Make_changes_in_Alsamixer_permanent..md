---
title: "Make changes in Alsamixer permanent."
date: 2010-02-14
forum: Multimedia Software
---

### Post by The__Doctor on 2010-02-14
Every time I turn on my laptop, the alsamixer settings get reset. How do I make the changes permanent?

---

### Post by Menthu_Rae on 2010-02-14
> **The__Doctor said:**
> Every time I turn on my laptop, the alsamixer settings get reset. How do I make the changes permanent?

```
sudo alsamixer
sudo alsactl store
```

or

```
alsamixer
alsactl store
```

---

### Post by The__Doctor on 2010-02-15
I entered that code in the terminal but it doesn't work.

---

### Post by fabio.hipolito on 2012-04-04
Hello,

same problem here. I have a ASUS F3Jc running Ubuntu 11.10.

Best regards.

---

