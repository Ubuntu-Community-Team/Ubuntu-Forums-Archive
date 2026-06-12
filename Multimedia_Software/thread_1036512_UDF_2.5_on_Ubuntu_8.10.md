---
title: "UDF 2.5 on Ubuntu 8.10"
date: 2009-01-10
forum: Multimedia Software
---

### Post by Beaon on 2009-01-10
Hello Guys,

I am fairly new to ubuntu and not completly familiar with linux in general but feel pretty confident I can eventually do what I want to do.

In short I would like to get UDF 2.5 running on my Ubuntu 8.10 64bit.

I found the following thread on the forums..
[http://209.85.173.101/translate_c?hl=en&sl=no&u=http://ubuntuforums.org/showthread.php%3Ft%3D718744&prev=/search%3Fq%3D/udf-filesystem-2.5/src/udfdecl.h:4:26:%2Berror:%2Blinux/udf_fs.h:%2BNo%2Bsuch%2Bfile%2Bor%2Bdirectory%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3DD3q%26sa%3DG&usg=ALkJrhhUZv4LQb_O9UHRmk1XvTcrtGP5VQ](http://209.85.173.101/translate_c?hl=en&sl=no&u=http://ubuntuforums.org/showthread.php%3Ft%3D718744&prev=/search%3Fq%3D/udf-filesystem-2.5/src/udfdecl.h:4:26:%2Berror:%2Blinux/udf_fs.h:%2BNo%2Bsuch%2Bfile%2Bor%2Bdirectory%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3DD3q%26sa%3DG&usg=ALkJrhhUZv4LQb_O9UHRmk1XvTcrtGP5VQ)

However when I try to run Make, I get the following errors.

I am trying to do this without doing any custom kernel stuff. I'm not that advanced! :)

Here are the errors I get from make.

```
crunch@Crunch:~/Documents/udf-filesystem-2.5$ sudo make
[sudo] password for crunch: 
make -C /lib/modules/2.6.27-9-generic/build M=/home/crunch/Documents/udf-filesystem-2.5 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/crunch/Documents/udf-filesystem-2.5/src/balloc.o
In file included from /home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:22:
/home/crunch/Documents/udf-filesystem-2.5/src/udfdecl.h:4:26: error: linux/udf_fs.h: No such file or directory
In file included from /home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:28:
/home/crunch/Documents/udf-filesystem-2.5/src/udf_i.h: In function ‘UDF_I’:
/home/crunch/Documents/udf-filesystem-2.5/src/udf_i.h:7: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/udf_i.h:7: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/crunch/Documents/udf-filesystem-2.5/src/udf_i.h:7: warning: initialization from incompatible pointer type
/home/crunch/Documents/udf-filesystem-2.5/src/udf_i.h:7: error: invalid use of undefined type ‘struct udf_inode_info’
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c: In function ‘__load_block_bitmap’:
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:109: error: implicit declaration of function ‘udf_debug’
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c: In function ‘udf_table_free_blocks’:
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:446: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:512: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:514: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:543: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:556: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:557: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:569: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:597: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c: In function ‘udf_table_prealloc_blocks’:
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:633: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:635: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:642: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c: In function ‘udf_table_new_block’:
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:698: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:700: error: dereferencing pointer to incomplete type
/home/crunch/Documents/udf-filesystem-2.5/src/balloc.c:715: error: dereferencing pointer to incomplete type
make[3]: *** [/home/crunch/Documents/udf-filesystem-2.5/src/balloc.o] Error 1
make[2]: *** [/home/crunch/Documents/udf-filesystem-2.5/src] Error 2
make[1]: *** [_module_/home/crunch/Documents/udf-filesystem-2.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2

```

Any help is much appreciated. It appears that I am missing some things,.

---

### Post by bobbob1016 on 2009-01-10
Welcome to the forums, Beaon.  Not to be critical, but you should say what UDF 2.5 is.  A quick google says it is a caricature creator.  You should also try to post in the right place, this would go under general help.

From the looks of it, you are trying to compile something.  If you are going for the caricature thing, which I'm guessing is a windows application, click Applications -> Add/Remove, then install wine.  Then get the .exe for UDF creator, and double click, it should show up under Applications -> Wine

---

### Post by Beaon on 2009-01-10
Hello bobbob1016,

Criticism is welcome. I'll be happy to move the post to a more appropriate location but before I do that I want to be sure lest I just annoy some other veterans else where.


This is in regards to Universal Disk Format 2.5 which is required to read Blu-Ray Disks. I just assumed this would best be located under Multi-media.


A quick google search on UDF will send you here. If you search for UDF+ubuntu you will end up with alot of incomplete posts on the ubuntuforums.org website. I am just trying to pick-up where the trail apparently ends.

Here is the information UDF.
[http://en.wikipedia.org/wiki/Universal_Disk_Format](http://en.wikipedia.org/wiki/Universal_Disk_Format)

The reason I am doing this is because of the recommendations from this article.
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

Like other folk, i got to the point where he states that UDF 2.0 does not work and therefore you must upgrade to UDF 2.5. The specific quote is here.
> A UDF 2.5 filesystem driver (the UDF driver included up to 8.04 Hardy Heron only supports UDF 2.0). A driver for Feisty Fawn's 2.6.20-15 kernel is attached to this page. Copy it to /lib/modules/2.6.20-15-generic/kernel/fs/udf/udf.ko. 

Should I repost this in general?

Also you mentioned it's trying to compile something. How can I find what I am missing to complete the compile process?

Thanks bobbob1016

---

### Post by mc4man on 2009-01-11
>  Entering directory `/usr/src/linux-headers-2.6.27-9-generic

That module your trying to make is only for linux-headers-2.6.24-xx-generic,(hardy)
Will not work on Intrepid

---

### Post by Beaon on 2009-01-11
So do I need to build a custom kernel?

---

### Post by Beaon on 2009-01-13
Does any one have any information related to getting this running on my current kernel?

---

### Post by mc4man on 2009-01-13
> That module your trying to make
What I meant to say was that patch your trying to use is for 2.6.24

I just installed intrepid a few days ago, it seems to recognize a hd-dvd just fine. It seems it has support for UDF 2.5.

**Some** vista live system dvd's may not be workable though, will have to ck.



Edit; 
a quick test shows hddvd, blu-ray and a 'clean' udf 2.5 data dvd created by Imgburn are all readable on Intrepid, a vista 'live system' disk formated to udf 2.5 isn't.

On a hardy install with a patched udf module the vista 2.5 disk is readable.

Maybe because the intrepid kernel didn't include the additional udf patch as seen here (lower part of page., though it was intended for vista 2.01
Or maybe some other reason.

[http://sourceforge.net/tracker/index.php?func=detail&aid=1882910&group_id=295&atid=300295](http://sourceforge.net/tracker/index.php?func=detail&aid=1882910&group_id=295&atid=300295)

---

### Post by Beaon on 2009-01-15
I am foolish and have wasted your time. "Intrepid" reads blue-rays just fine. 

Now if I can just get DumpHD to work so I can actually watch movies!!](*,)

---

### Post by mc4man on 2009-01-15
> Now if I can just get DumpHD to work so I can actually watch movies

[http://forum.doom9.org/forumdisplay.php?f=63](http://forum.doom9.org/forumdisplay.php?f=63)

---

