---
title: "Cannot see printer status with fwrite"
date: 2011-08-08
forum: Multimedia Software
---

### Post by mensfort on 2011-08-08
I try to use a printer on the USB port, which shows as /dev/usblp1. When I print, the output is correct. However, I cannot see the printer status correct. Following example shows the same for paper or no paper. What am I doing wrong:


    FILE *F= fopen("/dev/usblp1", "w");
    int status=fwrite("--\n\n\n", 1,5, F);


chmod is 666. Also, the group is correct.

---

