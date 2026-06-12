---
title: "procps error in upgrade"
date: 2010-06-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zika on 2010-06-09
```
:~$ cat error.txt 
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 procps
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up procps (1:3.2.8-9ubuntu1) ...
start: Job failed to start
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 procps
...
The following partially installed packages will be configured:
  procps 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up procps (1:3.2.8-9ubuntu1) ...
start: Job failed to start
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 procps
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up procps (1:3.2.8-9ubuntu1) ...
start: Job failed to start
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 procps
```

---

### Post by taavikko on 2010-06-09
safe-upgrading here as I write and it goes through without errors...

try cleaning cache and re-instaallation of it.

---

### Post by yelo3 on 2010-06-09
I have a solution to this.
The thing that fails is the service startup, which resides in /etc/init/sysctl.conf which executes this command: cat /etc/sysctl.d/*.conf /etc/sysctl.conf | sysctl -p -
so you can execute it by yourself to see if there is an error (like in my case I had a swappiness key that does not work, so I removed it)

```
cat /etc/sysctl.d/*.conf /etc/sysctl.conf | sudo sysctl -p -
```

---

### Post by zika on 2010-06-09
> **taavikko said:**
> safe-upgrading here as I write and it goes through without errors...

try cleaning cache and re-instaallation of it.You can see (after "...") the result of clean cache re-try...

---

### Post by taavikko on 2010-06-09
> **zika said:**
> You can see (after "...") the result of clean cache re-try...

I should really take a nap.... woke up 3am...

---

### Post by zika on 2010-06-09
> **yelo3 said:**
> I have a solution to this.
The thing that fails is the service startup, which resides in /etc/init/sysctl.conf which executes this command: cat /etc/sysctl.d/*.conf /etc/sysctl.conf | sysctl -p -
so you can execute it by yourself to see if there is an error (like in my case I had a swappiness key that does not work, so I removed it)

```
cat /etc/sysctl.d/*.conf /etc/sysctl.conf | sudo sysctl -p -
```Bingo. In /etc/sysctl.d/10-ptrace.conf there was a line: kernel.ptrace_scope = 1 that caused the trouble. After I commented it, everything is OK. Thank You!

---

### Post by taavikko on 2010-06-09
> **zika said:**
> Bingo. In /etc/sysctl.d/10-ptrace.conf there was a line: kernel.ptrace_scope = 1 that caused the trouble. After I commented it, everything is OK. Thank You!

I have the same, but it didn't affect upgrade here?

---

### Post by dino99 on 2010-06-09
no trouble on my end :p but i'm waiting for xorg feedback before update it

---

### Post by zika on 2010-06-09
> **taavikko said:**
> I have the same, but it didn't affect upgrade here?Who knows. It gave error in my case. I've commented it and... (That was in 2.6.35-999)

---

### Post by taavikko on 2010-06-09
> **zika said:**
> Who knows. It gave error in my case. I've commented it and... (That was in 2.6.35-999)

Aah, self-inflicted wound ;)

---

### Post by zika on 2010-06-09
> **taavikko said:**
> Aah, self-inflicted wound ;)Yeap, it might be... I'm trying this, now on 2.6-35-ubuntu but it doesn't give the error any way, now, the wound self-healed...

But, from the bug filled, I'm not the only one... No way that all the others are using 2.6.35-999, also...

---

### Post by DougieFresh4U on 2010-06-09
> **taavikko said:**
> Aah, self-inflicted wound ;)

I had that same error yesterday ):P

---

