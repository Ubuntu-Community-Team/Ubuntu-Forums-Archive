---
title: "building the fglrx module"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by Absurd on 2007-01-08
I'm following the tutorial [here](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) on how to install the driver manually.

When I get to entering "sudo module-assistant build fglrx" I get the error:

> make[2]: Entering directory                                                &#9618;
                        &#9474; `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'                      &#9618;
                        &#9474; make[2]: Makefile: No such file or directory                               &#9618;
                        &#9474; make[2]: *** No rule to make target `Makefile'.  Stop.                     &#9618;
                        &#9474; make[2]: Leaving directory                                                 &#9618;
                        &#9474; `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'

I actually took a look in /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/ and found a symlinked makefile.

How can I fix this?

---

### Post by Absurd on 2007-01-08
nevermind, I fixed it. :D

---

### Post by marioquark on 2008-03-01
thank you to explain us how you did it.. :(

---

### Post by dennymallow on 2008-05-02
Please, tell us how you fixed the problem, since I'm another user stuck with my X1650 512MB AGP and Hardy...

---

