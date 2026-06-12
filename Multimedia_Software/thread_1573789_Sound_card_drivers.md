---
title: "Sound card drivers?"
date: 2010-09-13
forum: Multimedia Software
---

### Post by RFrenette on 2010-09-13
I recently installed Ubuntu on a 2001 Dell Dimension 4300 desktop, with  a Santa Cruz 38FRH Sound Card, and have no sound. Wondering if anyone knows of a driver that will work with this system/card. I haven't been able to find one on-line.

Thanks,
Rob

---

### Post by Claus7 on 2010-09-13
Hello,

does this command produces any result?

```
lspci -nn | grep Audio
```

Regards!

---

### Post by RFrenette on 2010-09-13
It produces the following:

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)

Thanks

---

### Post by RFrenette on 2010-09-13
As much as I didn't want to do this, I installed VirtBox, then XP, then ran the card's installation software for Win, and it's working now.

---

### Post by Claus7 on 2010-09-14
Hello,

from this command it seems that your card is recognized. Have you "tampered with" the options? There are many reasons why your card is not working, even because it might be muted.

Have you tried the command alsamixer and play with the options there?

Regards!

---

