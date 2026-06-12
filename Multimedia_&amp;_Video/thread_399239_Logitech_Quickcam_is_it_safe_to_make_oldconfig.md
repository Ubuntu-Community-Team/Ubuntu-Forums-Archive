---
title: "Logitech Quickcam: is it safe to make oldconfig?"
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by skywatcher on 2007-04-02
I recently tried to install the qc-usb driver from qce-ga ([http://qce-ga.sourceforge.net/]("http://qce-ga.sourceforge.net/")).

I followed all the instructions, but when I run the 'sudo make all' step, an error is reported -- it tells me that

```
echo "         include/linux/autoconf.h or
include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel
src to fix  it.";
```

I checked to see if those files are missing, but they are both where they should be.

What I would like to know, is it safe to run 'make oldconfig && make prepare'? Won't this mess up something else?

---

### Post by gary441 on 2007-04-02
Hello
I'm actually having the same problem with qce-ga. 
I tried the "make oldconfig && make prepare" but nothing changed. Unless I have to recompile the  whole kernel again or reboot.

[EDIT]
I thought I'd add that I installed 2.6.20 kernel.  qce-ga works fine with the default kernel of 2.6.17-11-generic

---

### Post by skywatcher on 2007-04-02
Thanks gary441

It turns out that I also have 2.6.20 kernel --  so that seems to be the problem...

Cheers

---

