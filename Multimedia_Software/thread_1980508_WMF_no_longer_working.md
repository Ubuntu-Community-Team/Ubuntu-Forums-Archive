---
title: "WMF no longer working"
date: 2012-05-15
forum: Multimedia Software
---

### Post by Paddy Landau on 2012-05-15
In 10.04, WMF files worked correctly; GIMP was easily able to open them.

Then, in 11.04, WMF files no longer worked, but at least there was a workaround: you could convert them to EPS as follows.
```
wmf2eps --wmf-fontdir=/usr/share/fonts/type1/gsfonts -o *outputfile.eps* *inputfile.wmf*
```But now, to my horror, this does not work in 12.04. There is no error message; the command wmf2eps simply does not work.

I need to work on WMF files *by tomorrow*. Please, can you give any help?

---

### Post by Paddy Landau on 2012-05-18
New information:

I installed 10.04 and 10.10 into a virtual machine. For both, I fully updated; installed ubuntu-restricted-extras, gimp and gimp-data-extras; and restarted.

10.04 worked flawlessly, whereas 10.10 had the error. So, we know when the problem started.

---

### Post by Paddy Landau on 2012-05-19
I have raised a bug for this.

If it affects you, please [go to the bug and vote for it]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1001570") (the green writing near the top-left of the page).

---

