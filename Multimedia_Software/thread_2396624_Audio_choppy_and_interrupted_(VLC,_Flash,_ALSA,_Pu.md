---
title: "Audio choppy and interrupted (VLC, Flash, ALSA, Pulse)"
date: 2018-07-18
forum: Multimedia Software
---

### Post by hirscherne on 2018-07-18
Since a couple of days, I am experiencing interrupted audio playback on my box. There are small clicks and pops and sometimes, audio is interrupted completely.

I am currently running

```
$ uname -a
Linux TeurerSpass 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
$ cat /etc/issue
Ubuntu 18.04 LTS \n \l
```

I believe this is a Kernel-based problem because it affects audio from VLC, as well as audio from Flash.

My update history, as far as the Kernel is concerned:


[LIST]
[*]2018-07-14: Kernel 4.15.0-28 
[*]2018-07-18: Kernel 4.15.0-29 
[/LIST]

I first noticed these problems yesterday (2018-07-17) so I think the problems started with 4.15.0-28.

Here is the output of VLC when a larger dropout happens:

```

main warning: playback way too late (180536): flushing buffers
alsa error: cannot estimate delay: Input/output error
main warning: playback way too early (-1192030): playing silence
main debug: inserting 52568 zeroes
alsa warning: cannot write samples: Broken pipe

```

Any ideas what this could be?

I am also noticing slightly reduced responsiveness. Maybe the kernel is not allocating enough time to VLC?

Thanks for any ideas.

---

### Post by hirscherne on 2018-07-19
I have tried to switch back to the previously installed 4.15.0-26 kernel but couldn't. Does anybody know how to revert to that kernel?

```

$ sudo apt -y install linux-image-4.15.0-26-generic:amd64  linux-modules-extra-4.15.0-26-generic:amd64 linux-modules-4.15.0-26-generic:amd64
[sudo] password for …: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-4.15.0-26-generic:amd64
E: Couldn't find any package by glob 'linux-image-4.15.0-26-generic'
E: Couldn't find any package by regex 'linux-image-4.15.0-26-generic'
E: Unable to locate package linux-modules-extra-4.15.0-26-generic:amd64
E: Couldn't find any package by glob 'linux-modules-extra-4.15.0-26-generic'
E: Couldn't find any package by regex 'linux-modules-extra-4.15.0-26-generic'
E: Unable to locate package linux-modules-4.15.0-26-generic:amd64
E: Couldn't find any package by glob 'linux-modules-4.15.0-26-generic'
E: Couldn't find any package by regex 'linux-modules-4.15.0-26-generic'
```

---

### Post by #&amp;thj^% on 2018-07-19
I think you will find it already installed:
```
apt search linux-image-4.15.0-26-generic
Sorting... Done
Full Text Search... Done
linux-image-4.15.0-26-generic/**_now 4.15.0-26.28 amd64 [installed,local]_**
  Signed kernel image generic

```
And your code you used>> should have dropped the <amd64>IE:
```
sudo apt install linux-image-4.15.0-26-generic linux-modules-extra-4.15.0-26-generic linux-headers-4.15.0-26-generic
```

---

### Post by hirscherne on 2018-07-19
> **1fallen said:**
> I think you will find it already installed:
```
apt search linux-image-4.15.0-26-generic
Sorting... Done
Full Text Search... Done
linux-image-4.15.0-26-generic/**_now 4.15.0-26.28 amd64 [installed,local]_**
  Signed kernel image generic

```


Thanks. IIRC that didn't work when I tried it. However, I found 4.15.0-24 [here](https://packages.ubuntu.com/bionic/amd64/linux-modules-4.15.0-24-generic/download). However, that Kernel has the same problem.

So it's not the Kernel.

---

### Post by hirscherne on 2018-07-19
In Java-land, there is a program that tracks when the VM is not responsive, for example because it's garbage collecting. Is there something like that for Linux? I.e. is the Kernel ever stopping user-space processes to care about itself?

---

### Post by hirscherne on 2018-07-22
Here is the output of the alsa-info.sh script:

[http://www.alsa-project.org/db/?f=3516cc68f781ad1079c542aaf4f08a1006f54bd7](http://www.alsa-project.org/db/?f=3516cc68f781ad1079c542aaf4f08a1006f54bd7)

Maybe this helps.

---

### Post by hirscherne on 2018-07-22
I have strace'd VLC and there is a message about futex timed out or so. I'll look up what this is but could this have something to do with it?

```

futex(0x7f3d900013d0, FUTEX_UNLOCK_PI_PRIVATE) = 0
futex(0x7f3d6c0166e0, FUTEX_WAIT_PRIVATE, 0, {tv_sec=0, tv_nsec=25529624}) = -1 ETIMEDOUT (Connection timed out)
futex(0x7f3d6c009b90, FUTEX_WAKE_PRIVATE, 1) = 0
getpid()                                = 5781
getpid()                                = 5781
write(3, "main warning: playback way too l"..., 63) = 63 <-- This is what gets written to VLC's log

```

---

### Post by hirscherne on 2018-08-22
FWIW I've somehow managed to mangle my installation and had to do a complete Ubuntu reinstall. I'm not 100 % happy with Bionic Beaver (switching workspaces doesn't seem to affect the second monitor, for example) but at least the sound is uninterrupted now.

---

