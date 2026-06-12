---
title: "Ongoing Memory problems with nVidia proprietary driver"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by macstevejb on 2011-04-06
the following bugs refer:

[https://bugs.launchpad.net/bugs/725434](https://bugs.launchpad.net/bugs/725434)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/735482](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/735482)

My system runs an nvidia GeForce 6100 graphics card. Ubuntu 11.04 runs fine on classic gnome with open graphics driver but as soon as I install the nvidia proprietary driver, RAM usage increases by over 100%, whether it be in Unity, Unity 2D or Classic gnome environments.

Clearly there is a problem with Ubuntu 11.04 running the latest nvidia proprietary drivers.

Hope this will be fixed before final release because there must be an awful lot of users out there with nvidia cards who will think twice about 11.04 if it continues to pose such huge memory problems.

Anybody with similar problems have an ideas about a possible fix?

regards

---

### Post by ratcheer on 2011-04-06
My system is running just fine, but I do see that it is using almost all (85%) of the RAM. The bug you pointed to is a dup of bug 725434, which has been open since Feb 26. I have added myself to the bug report.

I am using nVidia 270.30.

Tim

---

### Post by Bobhuber on 2011-04-06
> **macstevejb said:**
> the following bugs refer:

[https://bugs.launchpad.net/bugs/725434](https://bugs.launchpad.net/bugs/725434)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/735482](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/735482)

My system runs an nvidia GeForce 6100 graphics card. Ubuntu 11.04 runs fine on classic gnome with open graphics driver but as soon as I install the nvidia proprietary driver, RAM usage increases by over 100%, whether it be in Unity, Unity 2D or Classic gnome environments.

Clearly there is a problem with Ubuntu 11.04 running the latest nvidia proprietary drivers.

Hope this will be fixed before final release because there must be an awful lot of users out there with nvidia cards who will think twice about 11.04 if it continues to pose such huge memory problems.

Anybody with similar problems have an ideas about a possible fix?

regards
Try using the x-org edgers ppa . This will install the 270.30 drivers which are the only ones I have found that come close to working.

---

### Post by Harry33 on 2011-04-06
> **Bobhuber said:**
> Try using the x-org edgers ppa . This will install the 270.30 drivers which are the only ones I have found that come close to working.

Actually Natty repos contain exactly the same nvidia-current 270.30 driver.

---

### Post by ratcheer on 2011-04-06
After installing today's Natty software updates, my system is using much less RAM, but much more swap space. I am undecided whether that is good or bad.

```
      1025048 K total memory
       586980 K used memory
       250488 K active memory
       255064 K inactive memory
       438068 K free memory
        25024 K buffer memory
       212080 K swap cache
      2000056 K total swap
       565136 K used swap
      1434920 K free swap

```

Tim

---

### Post by mc4man on 2011-04-06
> After installing today's Natty software updates, my system is using much less RAM, but much more swap space.
generally i'd consider the use of swap as not good, though it may not always cause slowdowns.

The bug is well understood, there are several ways to be addressed and it will be.
I believe it's a matter of finding the best overall  solution, certainly not that ones don't exist already.
While waiting i have fixed here using one method on a machine that would be affected (p4 w/ 1GB ram
Ex. - before and after, use at login
```
doug@doug-alienware:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1000        809        190          0         55        182
-/+ buffers/cache:        571        428
Swap:          284          0        284


doug@doug-alienware:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1000        469        531          0         56        182
-/+ buffers/cache:        230        769
Swap:          284          0        284
```

There is really no need for additional comments to the bug unless it concerns technical aspects of proposed solutions

---

### Post by macstevejb on 2011-04-07
mc4man:

could you tell me what your fix was please?

I also have a P4 machine.

regards

---

### Post by mc4man on 2011-04-07
> **macstevejb said:**
> mc4man:

could you tell me what your fix was please?

I also have a P4 machine.

regards
Mentioned a few times in bug - just rebuilt the cairo source package set removing the --with-gl option

Fairly simple though it requires a new libcairo2.symbols file or not all the packages will be built. (the ones needed

Then just replaced the ones I do use - 

libcairo2_1.10.2-2ubuntu1_i386.deb
libcairo2-dev_1.10.2-2ubuntu1_i386.deb
libcairo-gobject2_1.10.2-2ubuntu1_i386.deb
libcairo-script-interpreter2_1.10.2-2ubuntu1_i386.deb

(though recently got tired of protecting them from being updated so redid and bumped the package names like this

libcairo2_1.10.2-2ubuntu1+nmu1_i386.deb
libcairo2-dev_1.10.2-2ubuntu1+nmu1_i386.deb
libcairo-gobject2_1.10.2-2ubuntu1+nmu1_i386.deb
libcairo-script-interpreter2_1.10.2-2ubuntu1+nmu1_i386.deb

I really can't see them not fixing this shortly one way or the other..,

---

### Post by mc4man on 2011-04-08
Due to late date a fix will be happening shortly - the default cairo will be rebuilt without gl,  gl enabled cairo packages will be in a ppa for those that have use for.
Hopefully by 11.10 a nvidia side or other solution will happen

---

### Post by Harry33 on 2011-04-08
> **mc4man said:**
> Due to late date a fix will be happening shortly - the default cairo will be rebuilt without gl,  gl enabled cairo packages will be in a ppa for those that have use for.
Hopefully by 11.10 a nvidia side or other solution will happen

New cairo (1.10.2-2ubuntu2) is in Natty repos now.

---

### Post by mc4man on 2011-04-08
This should provide some  relief and leeway to lower ram setups though...
if using unity  - 
compiz currently does use a fair amount of mem to start and it will increase in general a small amount over time and normal usage

Use of the dash, .places, Alt+F2, various actions on and in the launcher, possibly the global menu  will also increase a bit each time. 
Shouldn't become a big issue unless online for an extended period (maybe, - haven't had a chance to see if it will eventually 'cap' out or not.

---

### Post by ratcheer on 2011-04-08
I don't see much relief. Natty is fully updated, as of now. With only the Unity desktop, a terminal, and Firefox 4 running, my memory usage is about like it was, originally:

```
      1025048 K total memory
       849388 K used memory
       493148 K active memory
       253528 K inactive memory
       175660 K free memory
        63000 K buffer memory
       374820 K swap cache
      2000056 K total swap
         5796 K used swap
      1994260 K free swap

```

RAM usage is back up to about 85% and swap usage only about 6 MB.

Tim

---

### Post by mc4man on 2011-04-08
> I don't see much relief. Natty is fully updated, as of now. With only the Unity desktop, a terminal, and Firefox 4 running, my memory usage is about like it was, originally:


Did you do a full restart yet?

---

### Post by ratcheer on 2011-04-08
> **mc4man said:**
> Did you do a full restart yet?

No, since Ubuntu didn't demand a restart, I thought logoff and logon would be sufficient. I will reboot and report back. Thanks.

Tim

---

### Post by cariboo on 2011-04-08
I just updated to the latest libcairo, and my memory usage dropped considerably, with the same apps running.

Before update and reboot:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1917         90          0         42        246
-/+ buffers/cache:       1627        380
Swap:         1906        127       1779
```

after:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1349        658          0         56        583
-/+ buffers/cache:        709       1298
Swap:         1906          0       1906
```

---

### Post by ratcheer on 2011-04-08
After reboot, with FF 4, terminal, and Unity:

```
      1025048 K total memory
       627912 K used memory
       330848 K active memory
       208960 K inactive memory
       397136 K free memory
        34036 K buffer memory
       229600 K swap cache
      2000056 K total swap
            0 K used swap
      2000056 K free swap

```

Somewhat better. compiz is using quite a bit less memory. No swap is being used.

Thanks,
Tim

---

### Post by mc4man on 2011-04-08
While not quite sure yet I believe compiz mem use (accumulated over use/time), is a bit better on a fresh iso install today than a 3 week old updated, though  the 3 wk. old is a bit better behaved.
(ultimately the state of   now (fresh install) is what matters

@ratcheer - 
it may be interesting to see what your 'base' mem use is, if interested install sysstat
Then do a _restart_, after logging, wait about 30 sec. then open a terminal and run this
 ```
pidstat -r -p ALL > base_mem.log
```

You'll get 1 report in home folder

---

