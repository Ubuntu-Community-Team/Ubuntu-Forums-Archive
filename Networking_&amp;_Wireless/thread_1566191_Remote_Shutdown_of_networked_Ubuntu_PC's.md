---
title: "Remote Shutdown of networked Ubuntu PC's"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by Linuxson25 on 2010-09-02
Hi

I will be running a network of +- 35 Ubuntu pc's from next year on. I have already started setting up remote desktop viewing utilities, but I now need a way to remotely shut down all the pc's at the same time, with a simple command as Admin. Setting up scripts to execute at a certain time is not gonna help, as the online time wont be the same all the time. I want to avoid having to remotely shut down each and every pc, as this will take quite a lot of time. Any help will be greatly appreciated

Thanx

---

### Post by BkkBonanza on 2010-09-02
One option, you could look into pssh (Parallel ssh) - this is ssh for multiple machines at once. It's in the repos. 

[http://www.theether.org/pssh/docs/0.2.3/pssh-HOWTO.html](http://www.theether.org/pssh/docs/0.2.3/pssh-HOWTO.html)

pssh -h hostlist sudo poweroff

ClusterSSH another similar option.

You would want to use keys to authenticate either way.

---

### Post by Linuxson25 on 2010-09-04
> **BkkBonaza said:**
> One option, you could look into pssh (Parallel ssh) - this is ssh for multiple machines at once. It's in the repos. 

[http://www.theether.org/pssh/docs/0.2.3/pssh-HOWTO.html](http://www.theether.org/pssh/docs/0.2.3/pssh-HOWTO.html)

pssh -h hostlist sudo poweroff

ClusterSSH another similar option.

You would want to use keys to authenticate either way.
Thanx, I will definitely give it a try. Will only be able to give feedback by about end Jan next year :)

---

### Post by dE_logics on 2010-09-04
Using SSH make a shell script - 

```
ssh user@x.x.x.x < file
ssh user@x.x.x.x < file
ssh user@x.x.x.x < file
```

The file contains ```
halt;exit
```

I don't remember the format... sorry.

---

