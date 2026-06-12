---
title: "make: Nothing to be done for `all'. while compiling my first hello world kernel modul"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by sunandi on 2011-07-02
Hi All,
This might not be the correct category to post this thread but couldnt find the correct category for this question so posting here.

1. I am following the basic tutorial to learn to compile my first hello-world kernel module.
========================
/*
   first_mod.c
   My first kernel module.
*/

#include <linux/module.h> /* Needed by all modules */
#include <linux/kernel.h> /* Needed for KERN_INFO*/
int init_module(void)
{
   printk(KERN_INFO "Hello world 1.\n");

   /* 
    * A non 0 return means init_module failed; module can't be loaded. 
    */
   return 0;
}

void cleanup_module(void)
{
   printk(KERN_INFO "Goodbye world 1.\n");
}

========================

and Makefile:
=========================
obj-m += first_mod.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
=========================

but when i do make it gives me this error:
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$ ll
total 16
drwxr-xr-x 2 sudipto sudipto 4096 2011-07-02 20:47 ./
drwxr-xr-x 4 sudipto sudipto 4096 2011-07-02 19:52 ../
-rw-r--r-- 1 sudipto sudipto  396 2011-07-02 20:13 first_mod.c
-rw-r--r-- 1 sudipto sudipto  173 2011-07-02 20:47 Makefile
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$ make
make: Nothing to be done for `all'.
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$

Help will be heavily appreciated

2. Also please suggest the correct forum to post this question

---

### Post by chili555 on 2011-07-02
[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44) might be more appropriate.

---

