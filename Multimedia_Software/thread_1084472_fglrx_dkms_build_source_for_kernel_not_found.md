---
title: "fglrx dkms build: source for kernel not found"
date: 2009-03-02
forum: Multimedia Software
---

### Post by Eremit on 2009-03-02
I have a problem when installing the fglrx driver. 
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

```
$ sudo dkms build -m fglrx -v 8.582 -k `uname -r`

Error! Your kernel source for kernel 2.6.27-12-generic cannot be found at
/lib/modules/2.6.27-12-generic/build or /lib/modules/2.6.27-12-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.

```

Any ideas?

---

### Post by binbash on 2009-03-02
I guess you need linux-headers match with your kernel.

---

### Post by Eremit on 2009-03-03
Thanks that helped!

---

