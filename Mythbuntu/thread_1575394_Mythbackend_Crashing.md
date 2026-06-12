---
title: "Mythbackend Crashing"
date: 2010-09-15
forum: Mythbuntu
---

### Post by cabbage on 2010-09-15
Hi,

I went to watch something on mythtv this evening and the machine failed to boot. In fact it seemed to reboot a few times by itself before finally sitting at the gdm logon.

Looking in the logs I've got lots of these:

```
Sep 15 21:10:58 localhost kernel: [   17.451778] mythbackend[1630]: segfault at 6df0fb80 ip 00bf79cf sp bfa0b534 error 4 in ld-2.10.1.so[bef000+1b000]
```

I tried doing an update which installed the latest 0.23-fixes packages but I'm still getting the crash.

I wonder if something on the disk has got corrupt?

The only other thing I'm seeing now is:

```
Sep 15 21:33:59 localhost kernel: [ 1398.677749] vmap allocation for size 819200 failed: use vmalloc=<size> to increase size.
```

There aren't any other errors in dmesg - apache and mysql are running fine, and X starts up. Just no auto login and mythbackend!

Any ideas or suggestions would be gratefully received!


Thanks,

Cabbage.

---

### Post by klc5555 on 2010-09-15
Not sure if it helps you, but could be this bug here: [https://bugs.launchpad.net/ubuntu/+source/bash/+bug/452175](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/452175)

But if the two error messages are related, you might want to up the size of the vmalloc option in grub --it's running out of virtual memory to allocate at boot.

---

### Post by cabbage on 2010-09-17
I ended up re-imaging (thanks to Clonezilla) my root file system and everything was OK.

So I guess the disk had a funny turn (it is a Compact Flash card after all!).

---

