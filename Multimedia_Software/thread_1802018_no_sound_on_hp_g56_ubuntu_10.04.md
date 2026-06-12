---
title: "no sound on hp g56 ubuntu 10.04"
date: 2011-07-11
forum: Multimedia Software
---

### Post by bh89 on 2011-07-11
Hi,

I recently installed ubuntu 10.04 on a hp g56 laptop, and the audio doesn't work. i tried to follow the "comprehensive sound problem" guide but i got stuck on step 3, i couldn't find the correct driver for my machine. I was just wondering if anyone could help me fix this?

thanks.

---

### Post by bh89 on 2011-07-12
?

---

### Post by lidex on 2011-07-14
> ?
;)
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

