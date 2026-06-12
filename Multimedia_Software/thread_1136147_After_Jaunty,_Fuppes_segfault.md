---
title: "After Jaunty, Fuppes segfault"
date: 2009-04-24
forum: Multimedia Software
---

### Post by tgilbert328 on 2009-04-24
Hi all.  I searched the forums, but I seem to be the only one reporting this problem.

I have used fuppes for a few months now successfully after some initial pain.  I upgraded to Jaunty today and now fuppes won't start.


```
            FUPPES - 0.629
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

== lib/Plugins/Plugin.cpp (110) :: Fri Apr 24 20:36:23 2009 ==
registered dlna profile plugin

Segmentation fault

```

dmesg shows this:

```

fuppes[15051]: segfault at 200 ip b7fa090d sp bffa8300 error 4 in ld-2.9.so[b7f8d000+1c000]

```

I typically run it as a service, fuppesd and running under sudo doesn't seem to help.

For the heck of it, here is uname -a

```
Linux localhost 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 i686 GNU/Linux
```

Anyone else experience or have any ideas?

Tim

---

### Post by oliver.greg@gmail.com on 2009-08-10
If you are using the PPA for Tim Kornhammar, I had the same issue...  

building from scratch worked fine, but I guess he stripped his binaries, so strace, ltrace provided no help why it was segfaulting...  It had to be a dependency that is there, but some simple version mismatch...

I found that installing his version, noting all of the dependencies, and install of of the -dev versions, then compiling from source worked...

-Greg

---

