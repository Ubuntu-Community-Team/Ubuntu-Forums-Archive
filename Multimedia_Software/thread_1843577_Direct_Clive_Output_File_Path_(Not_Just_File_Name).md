---
title: "Direct Clive Output File Path (Not Just File Name)"
date: 2011-09-13
forum: Multimedia Software
---

### Post by dniMretsaM on 2011-09-13
In Clive I know you can change the output file name with:
```
clive -O filename.flv 'http://www.url.com'
```

But how can I direct the out put to, say, ~/Videos/filename.flv?

---

### Post by dniMretsaM on 2011-09-14
Bump. Need this for a script I'm writing, so a fast answer would be great! Also, it could be CClive.

---

### Post by dniMretsaM on 2011-09-17
Solved. For those interested in the answer, here it is:
```
 clive **--save-dir=/path/to/save/directory/** -O videoname.extension 'http://url.com'
```

The bolded text being what I was looking for. Note that the save path and the name have to be separate. And I also get errors when don't use complete path names (like using ~/ instead of /home/joesmith/).

---

