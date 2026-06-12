---
title: "Need help with Kernel module compilation. (CONFIG_MODVERSIONS)"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by gopchandani on 2009-06-17
So, I pulled kernel source from a git (correspondes to 2.6.30 and also other dev patches happening) and executed make in the folder which resulted in compilation of the whole kernel and also modules in the source I downloaded. I am particular interested in ath9k wireless drivers. My machine has  kernel version  2.6.27-14 (Ubuntu 8.10) and it also already contains ath9k module. What I wanted to do was to download latest code for ath9k and replace/temporarily load the new module instead of one I have currently. I rmmod ath9k and tried to:

rakesh@pineapple:~/wireless-testing/drivers/net/wireless/ath/ath9k$ sudo insmod ath9k.ko

which results in:

insmod: error inserting 'ath9k.ko': -1 Invalid module format

and dmesg says:

[82375.379869] ath9k: no symbol version for struct_module

I looked up for this error: [http://lkml.org/lkml/2005/6/22/1](http://lkml.org/lkml/2005/6/22/1)

It says that I am supposed to have compiled the kernel being used and the module in question both with CONFIG_MODVERSIONS=Y

I do know that my .config file has CONFIG_MODVERSIONS=Y and I also verified it by checking the CRC tags which are generated as a result such configuration during compilation according to this: [http://www.skynet.ie/~mark/home/kernel/symbols.html](http://www.skynet.ie/~mark/home/kernel/symbols.html)

But what I am stuck on is how to compile a kernel module with CONFIG_MODVERSIONS=Y, I suppose when I run make for the pulled code, it uses this tag inherently for modules also but I am not sure about that.

So what am I missing her which would compile the module right to be plugged into a slightly older kernel version?

---

### Post by Ayuthia on 2009-06-17
From what I am understanding, you are compiling the 2.6.30 kernel with ath9k and then taking the module and placing it into the 2.6.27-14 kernel.  That generally does not work because they were compiled using different source codes.  I think what you are wanting to do is patch the 2.6.27-14 kernel with the ath9k changes and then compile the 2.6.27-14 source with those changes.  I am not for sure about how easy that is to do.

I could be wrong about this though.  You might be better off just using the newer kernel if you want to use the changes.

---

