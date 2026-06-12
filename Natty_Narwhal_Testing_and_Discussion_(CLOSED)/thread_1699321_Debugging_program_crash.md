---
title: "Debugging program crash"
date: 2011-03-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bestgun on 2011-03-03
I have a couple of questions about the debugging of a program crash.
I'm trying to understand how it works looking at [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash) but I still have some doubt.

I started trying to use it to obtain a valid stacktrace for a compiz crash that sometimes affects my system during the startup phase. After I installed the necessary dbgsym packages (in my case I downloaded compiz-core-dbgsym, compiz-plugins-extra-dbgsym, compiz-plugins-main-dbgsym and compiz-plugins-dbgsym) I try to reproduce the crash that typically occurs when I login into my account with the Ubuntu Destop Edition session.

My problems:
[list=1]
[*] Since my problem occurs during the login phase it's pretty hard intercept the compiz's process id before it crashes and attach it to dbg. Login in a different session type (like one without effects) and then use 
```
 *dbg>* run compiz --replace 
``` 
doesn't generates the crash :cry:
How can i use dbg to obtain the stacktrace with this type of crash?


[*] The only time that I was able to reproduce the crash and generate the stacktrace, it was full of *"No symbol table info available..."* messages before ending with a Segmentation fault.

I think a stacktrace with this type of messages is unuseful...so where is my error?
I have to download other dbgsym packages?
[/list]

thanks

---

### Post by bestgun on 2011-03-04
A good news, but it still not enough :(
At [https://wiki.ubuntu.com/DebuggingWithApportRetrace](https://wiki.ubuntu.com/DebuggingWithApportRetrace) there are some good info about how to use *apport-retrace*.
I tried to reproduce a valid backtrace with apport-retrace command but seems that my /var/crash/compiz.crash file doesn't have some important info.

```

andrea@Lynn:~$ sudo apport-retrace -o gdb/compiz/apport-retrace.txt /var/crash/_usr_bin_compiz.1000.crash 
ERROR: report file does not contain one of the required fields: CoreDump Package ExecutablePath

```

---

### Post by dino99 on 2011-03-04
have you tried some packages into synaptic: apport-retrace & pstack ?

---

### Post by bestgun on 2011-03-04
Tks dino99,
I've already tried (without success) with apport-retrace (see my prev post), but I will try with pstack and I let you know! 

really tks

---

### Post by bestgun on 2011-03-05
> **dino99 said:**
> have you tried some packages into synaptic: apport-retrace & pstack ?

OK, I tried to use **pstack** but the scarce documentation, with my limited knowledge of the subject do not help :-(

Citing the pstack manual * "Threads are not supported with the newer NPTL libpthread.so library." * and since I believe my libthread library uses NPTL I imagine pstack doesn't works on my system (with this libpthread library).

```

andrea@Lynn:~$ getconf GNU_LIBPTHREAD_VERSION
NPTL 2.13

```

In addition using ```
 nm /usr/lib/libpthread.a 
``` there is nothing that let me think that *"__pthread_threads_debug"  is defeined * as requested by pstack.

In short, this attempt also failed :cry:

---

### Post by MacUntu on 2011-03-05
I once did this by moving /usr/bin/compiz to /usr/bin/compiz.real and creating a wrapper /usr/bin/compiz that runs compiz.real under the control of gdb. Can't exactly tell you how that file looked like, but it definitely worked.

---

