---
title: "IPW 3945 With New Kernel 2.6.17"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by haani on 2006-06-24
does anyone know how to work ipw 3945 on the new compiled kernel 2.6.17? i tired it with ndiswrapper using windows driver but my kernel crashed!

---

### Post by haani on 2006-06-25
19 views still no reply!

---

### Post by Sloth on 2006-06-25
I got it working, no problems - I followed the instructions from sourceforge  and the only hitch was installing the ucode in /lib/firmware/2.6.17.1/.  Once I had that right, everything was smooth sailing.

---

### Post by ngeren on 2006-06-29
Tried booting it once .. No luck here .. I temporarily reverted back to 2.6.15 .. I guessing I'll be breaking and building my own 2.6.17 kernel since I can't trust Ubuntu's pre-packaged one.

---

### Post by Zanthius on 2006-08-31
Sloth  -  would it be a pain to list the steps that you did to get it working with the new kernel?

I have completed all the steps on that page, but it didn't work.  The kernel now doesn't compile.  Will start from scratch, but a howto, or some steps would be great (sorry, i'm a but of a newb)

Thanks.

---

### Post by djvishnu on 2006-09-07
I'd like to see a howto on building the dirvers as well, Im stuck here! :)

---

### Post by yonson_yon on 2006-09-24
> **Sloth said:**
> I got it working, no problems - I followed the instructions from sourceforge  and the only hitch was installing the ucode in /lib/firmware/2.6.17.1/.  Once I had that right, everything was smooth sailing.

yeah! how did you install that ucode? that's where i'm stuck. (not that i won't get stuck again...)

---

