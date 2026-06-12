---
title: "compiz 0.8.6"
date: 2010-08-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by scradock on 2010-08-04
New compiz packages 0.8.6 are available, but won't install without removing the compiz-fusion-plugins-extra package. Is there any news about when/whether this is just coming along later, or has it been merged into one of the packages currently available? If it's coming soon I would prefer to wait for it....

---

### Post by realzippy on 2010-08-04
This PPA seems to have  *compiz-fusion-plugins-extra 0.8.6*-0ubuntu1

[https://launchpad.net/~dashua/+archive/libcompizconfig](https://launchpad.net/~dashua/+archive/libcompizconfig)

---

### Post by plun on 2010-08-04
I just confirmed this bug....

[https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-extra/+bug/613340/](https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-extra/+bug/613340/)

---

### Post by scradock on 2010-08-05
To repeat the question - does anyone know when the compiz-fusion-plugins-extra package is going to be brought up to the 0.8.6 level so that I can accept the latest compiz* packages without removing c-f-p-extra and the additional plugins?

I have checked the bug plun noted - the complaint there is that after accepting the compiz*-0.8.6 packages one cannot install c-f-p-extra because it is still at 0.8.4. I have noted there that the best resolution would be to release an upgraded -extra package. Any news, anyone?

The compiz site says they are working to get all the plugins working for 0.9.2, so it doesn't sound as if the holdup is upstream.

---

### Post by realzippy on 2010-08-05
To repeat the answer-it is available through a PPA.
Please see post #2 of this thread,which seems to be ignored/not read by you.  

:-)

BTW,it works.

---

### Post by scradock on 2010-08-05
> **realzippy said:**
> To repeat the answer-it is available through a PPA.
Please see post #2 of this thread,which seems to be ignored/not read by you.  

:-)

BTW,it works.

Thanks - I had noted that. Especially during testing, I prefer not to use "unofficial" versions of core functionality, hence no ppas.

My question as addressed to the availability of an official, Canonical-provided version of a package that will allow other official, Canonical-provided packages to install and function correctly.

Does anyone know when such a package is going to be issued?

---

