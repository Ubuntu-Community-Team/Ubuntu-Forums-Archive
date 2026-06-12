---
title: "Solution for many wireless cards (incl. WG111v3)(WPA/WEP/no internet/etc. )"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by tarun1793 on 2009-08-08
Hi all,
i have a wg111v3 netgear usb adapter with which i face a lot of problems but at last i was able to fix it, It will correct and and let you work with ease on with many wireless cards .

Here's how is it going:
**STEP 1 : Gathering required files **

i have seen people posting codes to directly download and unzip files directly from the internet but my problem is that i am trying to get my connection work so how can i do this directly and being a newbie to linux i face a lot problems regarding the same . So the files below you can download on any other machine and then copy them to yours .


The reason behind the solution is that it update your linux kernel.

1. Goto  ```
 http://kernel.ubuntu.com/~kernel-ppa/mainline/   
```
and download the latest kernel files ( for now v.2.6.31.rc5) , and download the following files to the computer 
```
1. linux-headers-2.6.31-020631rc5_2.6.31-020631rc5_all.deb
2. linux-headers-2.6.31-020631rc5-generic_2.6.31-020631rc5_i386.deb
3. linux-image-2.6.31-020631rc5-generic_2.6.31-020631rc5_i386.deb    
```


2. copy them to your machine.

**2. Installing them**
 now they are all pre-compiled deb packages so you need not do much..

install them to your machine one by one keeping the order as specified below same 

```
1. linux-headers-2.6.31-020631rc5_2.6.31-020631rc5_all.deb
2. linux-headers-2.6.31-020631rc5-generic_2.6.31-020631rc5_i386.deb
3. linux-image-2.6.31-020631rc5-generic_2.6.31-020631rc5_i386.deb    
```

and then restart your system and you are done , it worked for me after everything as fails.  


Happy humanity...:KS

---

