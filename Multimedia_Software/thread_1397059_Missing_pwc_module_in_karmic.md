---
title: "Missing pwc module in karmic?"
date: 2010-02-02
forum: Multimedia Software
---

### Post by rbutler on 2010-02-02
Dear All,

I have an old Philips PCVC675K WebCam. It always worked with Ubuntu except the last karmic version. I even cannot modprobe the pwc module manually.

Is there someone who had the same issue and knows a solution?

Thanks,
Ralf

---

### Post by rbutler on 2010-02-03
Made further research and plugged the webcam in before booting. No success. As well I installed backport modules. No success either.
modprobe pwc leads to:
FATAL: Module pwc not found.

I guess this is the key issue here. What I don't understand is that the pwc module isn't found even though I made a clean installation of Ubuntu karmic. Or did they rename the module?

---

