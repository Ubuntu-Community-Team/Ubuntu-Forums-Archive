---
title: "After upgrade to Ubuntu, kernel 2.6.20-16-generic NVidia does not work"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by lzap on 2007-09-27
Hello all,

I did apt-get update upgrade and after reboot X Window wont come with error like "Cannot load nvidia" or something. Why did it brake?

Lukas

---

### Post by pbcartwright on 2007-09-28
when you install a new kernel you have to reinstall the NVidia drivers..
go to nvidia.com, download the new drivers, and read the REASDME and HOW-TO. Basically you just download the NVIDIA*.run and run:
sh NVIDIA*.run
follow the prompts to install it. Oh you need to stop the X-server ( kdm stop ) before running this.

---

### Post by amo-ej1 on 2007-09-28
Well the easy solution is simply getting the drivers ouf of apt. Do

```

e@lape:/tmp$ apt-cache search linux-restricted-modules

```

This will give you the choices, but the type should match the kernel specified in uname -a

```

e@lape:/tmp$ uname -a 
Linux lape 2.6.22-12-generic #1 SMP Sun Sep 23 18:11:30 GMT 2007 i686 GNU/Linux

```

So in this case it would

```

e@lape:/tmp$ sudo apt-get install linux-restricted-modules-2.6.22-12-generic 

```

---

### Post by lzap on 2007-10-05
Yes I know, but the strange thing is I have 2.6.20-16-generic kernel but there are NO 2.6.20-16-generic drivers.

I have to use -15 drivers for now...

---

### Post by lzap on 2007-10-05
Oh sorry, there is -16 version, but I have already installed it. Its installed but its not working.

---

