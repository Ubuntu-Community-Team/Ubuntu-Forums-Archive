---
title: "Realtek r8169"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by Dm-Bo on 2010-10-25
Hi all,

I break my mind trying to make Realtek-8169 works. I've downloaded driver source from realtek.com, but `make clean modules` returns
```

...
make[2]: Entering directory '/usr/src/linux-headers-2.6.35-22-generic'
scripts/Makefile.build.44: /src/Makefile: no such file or directory
...

```I've installed 'linux-headers-...' and 'linux-source' packages with no result.

Also, I meet this topic: [http://ubuntuforums.org/archive/index.php/t-1226628.html](http://ubuntuforums.org/archive/index.php/t-1226628.html) and this article: [http://www.jamesonwilliams.com/hardy-r8168](http://www.jamesonwilliams.com/hardy-r8168), but when I run it I get
```
Attemting to build the module... Could not build module.
```Please help me, after a 3-days brainstorm I close to suicide ](*,)

Ubuntu 10.10 Server, i386.

---

### Post by chili555 on 2010-10-25
Let's begin at the beginning. What about the built-in r8169 is not working for you? Please post some diagnostics:```
sudo lshw -C network
dmesg | grep -e 8169 -e eth0
ifconfig
sudo ethtool eth0
lsmod | grep 816
```Suicide is too messy.

---

### Post by Dm-Bo on 2010-10-25
> **chili555 said:**
> What about the built-in r8169 is not working for you?

Works only on 100M.

--

*SUDDENLY, *[http://ubuntuforums.org/archive/index.php/t-962405.html](http://ubuntuforums.org/archive/index.php/t-962405.html)

"the os looks for the Makefile in the /src/ directory on the root of the  hard drive instead of in the r8168-x.xxx.xx/src/ directory."

I've copied "src" directory to /, run "make clean modules", get a some kind of error, but r8169 appears in /src! Copying /src/* back to ~/r8169-xxx/src/, running last of commands and voilà! it works! At least, ethtool says so :)

Hundreds of hate to realtek coders and thanks to others :D

---

