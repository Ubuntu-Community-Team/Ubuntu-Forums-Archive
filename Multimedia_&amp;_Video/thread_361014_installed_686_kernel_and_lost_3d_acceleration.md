---
title: "installed 686 kernel and lost 3d acceleration"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by SpanishFranks on 2007-02-13
I installled the 2.6.15-27-686 kernel and have lost 3d acceleration (rebooting into 386 kernel works fine). I use fglrx as my gfx driver. Is there a special 686 build of fglrx I need to get, or a different 686 kernel? (I know I could just use the 386 kernel, but I want to do away with the 386 kernel and just use 686 ones)

---

### Post by lbyrd33 on 2007-02-13
Is your program approximately running everything else at the same speed or faster than on the 386?

---

### Post by SpanishFranks on 2007-02-13
big compiles using gcc seem marginally faster, but everything else seems to run at the same speed. (maybe its slightly faster, but I cant tell)

---

### Post by pay on 2007-02-13
You need to reinstall the fglrx kernel module for the 686 kernel. Just use the same steps that you did to install it in the first place and then the new kernel will be able to use it.

---

### Post by SpanishFranks on 2007-02-13
> **pay said:**
> You need to reinstall the fglrx kernel module for the 686 kernel. Just use the same steps that you did to install it in the first place and then the new kernel will be able to use it.

No luck so far. I did
```

sudo apt-get remove xorg-driver-fglrx fglrx-control
sudo apt-get install xorg-driver-fglrx fglrx-control

```

xorg-driver-fglrx still installed a i386 package

---

### Post by pay on 2007-02-13
> **SpanishFranks said:**
> No luck so far. I did
```

sudo apt-get remove xorg-driver-fglrx fglrx-control
sudo apt-get install xorg-driver-fglrx fglrx-control

```

xorg-driver-fglrx still installed a i386 package686 kernels can be i386 aswell. Also try ```
sudo depmod -a
```

---

