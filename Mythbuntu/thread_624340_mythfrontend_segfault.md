---
title: "mythfrontend segfault"
date: 2007-11-26
forum: Mythbuntu
---

### Post by onlynone on 2007-11-26
I've had mythbuntu running okay for about a week. It freezes sometimes while watching video, especially if I'm fast forwarding or rewinding. Usually a reboot will bring mythfrontend up fine, but the last time this happened I rebooted and just got a desktop instead of mythfrontend.

I tried running mythfrontend from a terminal and got an immediate segfault. I noticed that mythfrontend is a shell script wrapper around mythfrontend.real, so I copied the shell script to my ~/bin and modified the shebang line to: ```
#!/bin/sh -x
``` to get some shell debugging output. But I couldn't find anything that looked bad in that output.

Next I changed: ```
exec /usr/bin/mythfrontend.real "$@"
``` to:
```
exec strace /usr/bin/mythfrontend.real "$@"
``` But I couldn't find anything out of place in the strace output since I don't exactly know what to look for.

I've attached the output of running mythfrontend with both '-x' and 'strace' as log.txt.gz. I had to compress it to get under the file limits. For quick reference here just the shell debugging:
```

+ . /usr/share/mythtv/dialog_functions.sh
+ find_session
+ [ x = xtrue ]
+ [ x != x ]
+ xprop -root _DT_SAVE_MODE
+ grep  = \"xfce4\"$
+ DE=xfce
+ which zenity
+ DIALOG=/usr/bin/zenity
+ DIALOG_TYPE=zenity
+ which gksu
+ SU=/usr/bin/gksu
+ SU_TYPE=gksu
+ find_dialog
+ [ -z /usr/bin/zenity ]
+ [ -z /usr/bin/zenity ]
+ [ -z /usr/bin/zenity ]
+ find_su
+ [ -z /usr/bin/gksu ]
+ [ -z /usr/bin/gksu ]
+ [ -z gksu ]
+ check_groups
+ groups
+ grep --invert-match mythtv
+ [ -n  ]
+ IGNORE_NOT=0
+ [  = --service ]
+ [  != --service ]
+ [ 0 = 0 ]
+ exec strace /usr/bin/mythfrontend.real

```

And here is the last couple lines of the strace output:
```

fstat64(3, {st_mode=S_IFREG|0644, st_size=130364, ...}) = 0
mmap2(NULL, 129048, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb597e000
mmap2(0xb599c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1e) = 0xb599c000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb597d000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb597c000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb597b000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb597a000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb597a6c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb5c3b000, 4096, PROT_READ)   = 0
mprotect(0xb5d59000, 12288, PROT_READ)  = 0
mprotect(0xb5e92000, 385024, PROT_READ|PROT_WRITE) = 0
mprotect(0xb5e92000, 385024, PROT_READ|PROT_EXEC) = 0
mprotect(0xb6974000, 401408, PROT_READ|PROT_WRITE) = 0
mprotect(0xb6974000, 401408, PROT_READ|PROT_EXEC) = 0
mprotect(0xb6fac000, 4272128, PROT_READ|PROT_WRITE) = 0
mprotect(0xb6fac000, 4272128, PROT_READ|PROT_EXEC) = 0
munmap(0xb7fd8000, 41162)               = 0
set_tid_address(0xb597a708)             = 16226
set_robust_list(0xb597a710, 0xc)        = 0
rt_sigaction(SIGRTMIN, {0xb5d69300, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb5d69380, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="stivo", ...}) = 0
brk(0)                                  = 0x8197000
brk(0x81b8000)                          = 0x81b8000
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
Process 16226 detached

```

Any help is much appreciated.

---

### Post by onlynone on 2007-11-26
Specs:

Capture Card: Hauppauge WinTV PVR-350
CPU: VIA Nehemiah 1GHz
Memory: 1GB

---

### Post by superm1 on 2007-11-26
Please look in /var/crash for crash reports.

If they exist, then try to run

/usr/share/apport/apport-gtk

---

