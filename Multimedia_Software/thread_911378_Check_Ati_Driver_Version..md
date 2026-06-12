---
title: "Check Ati Driver Version."
date: 2008-09-05
forum: Multimedia Software
---

### Post by tracetheace on 2008-09-05
I've installed the official ATi driver and I want to know if there's a way to check this in terminal.

I know about fglrxinfo, but that doesn't return the value I'm looking for.
I'm looking for something along the lines of 'Catalyst 8.x'

Thanks.

---

### Post by nightawk on 2009-08-29
Me too - a year later, and no answers to your question so I'm not too hopeful! If by any chance you found a way please could you post it? Thankyou.

---

### Post by xzero1 on 2009-08-30
Try:
```
cat /var/log/Xorg.0.log | grep 'Driver Version'
```

---

### Post by nightawk on 2009-09-08
Thanks xzero1, that was very helpful.

---

### Post by hamiltino on 2013-04-07
> **xzero1 said:**
> Try:
```
cat /var/log/Xorg.0.log | grep 'Driver Version'
```

works!

---

### Post by oldos2er on 2013-04-07
Old thread closed.

---

